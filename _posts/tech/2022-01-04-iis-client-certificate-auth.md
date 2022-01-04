---
title: Configure Client Certificate Authentication for Asp.Net MVC Application
categories:
- ASPNet
- netframework
- IIS
aside: false
---
# Introduction
This article describes how to create a root and client certificate to be used for testing client certificate authentication with an application running on IIS express

# Background
The code used is ASP.NET MVC and PowerShell, the tools used are Visual Studio and PowerShell ISE. These steps apply to IIS express, but I am sure it would be similar for IIS. 

# The Problem 
A developer needs to have a local environment that is as close a match to the production conditions as possible. If client certificate authentication is required in production, it should be setup in local. There is no need to follow elaborate steps, using PowerShell to create the certificates and IIS express to run the application makes this easy.

# The Solution
## Overview Steps
    1. Create a test ASP.NET MVC app and enable SSL and verify that it works
    2. Enable client cert and try to access
    3. Try to access using a cert that isn't signed by a root authority
    4. Create cert that is signed by a root authority

## 1. Create a test ASP.NET MVC app and enable SSL and verify that it works
I am not going to spend much time on this. You should have Visual Studio installed and from there you can chose the Asp.net mvc template and create the default app. Enable SSL from the project properties window (see the resources below for steps). After you have the application configured, start it and verify that it is accesible running on local host at the specified port.

## 2. Enable client cert and try to access the application
Client security is enabled by updating the applicationhost.config file in the .vs hidden folder in your solution folder
Example path: E:\Projects\AppServiceClientCertTest\.vs\AppServiceClientCertTest\config\applicationhost.config

Open this file in visual studio or a text editor and add/update the below sslFlags and set iisClientCertificateMappingAuthentication to true

```xml

<security>
    <access sslFlags="Ssl, SslNegotiateCert, SslRequireCert" />
    ...
    <authentication>
        <iisClientCertificateMappingAuthentication enabled="true">
        </iisClientCertificateMappingAuthentication>
        ...
    </authentication>
</security>
```

Run the application again and you will see a 403.7 forbidden error

![Forbidden error when client cert is not available](/assets/img/2022-01-04_forbidden.png)

## 3. Create a certificate and use for access to application
To resolve the above error, we need to add a client certificate to the Current User's personal certifcate store location. This can be done with the below PowerShell script

Execute this script as an administrator to add a cert to the current user location
```powershell
New-SelfSignedCertificate -certstorelocation cert:\CurrentUser\My -DnsName "AnUnsignedTest"
```
Run the application again and you will be prompted to select a certificate. After selecting the recently added certificate, you will see a new forbidden message
![Forbidden error when client cert is not trusted](/assets/img/2022-01-04_forbidden40316.png)

This message means the client certificate is available, but it not trusted. In the next step we will add a trusted certificate, so this certificate can be removed using the MMC snapin console. 

## 4. Sign the certificate with a root authority and access the application
Execute the below PowerShell script to create a root cert, add that to the local machine store, and then create a user certificate signed by that root certificate

```powershell
#Create Root CERT

$rootcert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "testcert" -KeyUsage CertSign -FriendlyName "MyTestCA"
Write-host "Certificate Thumbprint: $($rootcert.Thumbprint)"

#This needs to be added to Trusted Root on all labcomputers 
Export-Certificate -Cert $rootcert -FilePath E:\Temp\AusmleTestCA.cer
Import-Certificate -FilePath E:\Temp\AusmleTestCA.cer -CertStoreLocation Cert:\LocalMachine\Root

#Create Your CERT
$rootca = Get-ChildItem cert:\LocalMachine\root | Where-Object {$_.Thumbprint -eq "$($rootcert.Thumbprint)"}
New-SelfSignedCertificate -certstorelocation cert:\CurrentUser\My -DnsName "AnUnsignedTest" -Signer $rootca -FriendlyName "AusmleTestClient"
```
After executing the below, run the application again. If you removed the previously created client cert, you will be prompted to select a new cert. If, there are mutliple certs installed in your user store, you can use a private browser window to see the cert selection option again.

## References
[Enable SSL in Visual Studio](https://www.ssl2buy.com/wiki/how-to-enable-ssl-in-visual-studio-for-a-net-project)
[Enable IIS express for client certs](https://improveandrepeat.com/2017/07/how-to-configure-iis-express-to-accept-ssl-client-certificates/)
[Setting uploadReadAheadSize](https://serverfault.com/questions/900211/iis-randomly-returns-413-request-entity-too-large-when-uploading-large-files-and)
