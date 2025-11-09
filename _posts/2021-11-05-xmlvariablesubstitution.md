---
title: .NET web.config Update via ADO Deployment Pipeline
date: 2021-11-05
categories: [Azure, DevOps, Pipelines]
tags: [azure, devops, pipelines]     # TAG names should always be lowercase
---

A common pattern in DevOps is to have multiple environments for running an application. Environments should always have their configuration values specified in web configuration files, not hardcoded into the code. But how can you deploy the same application to multiple environments without having separate web config files for each environment?

## Scenario
An application team wants to deploy their application to a test and a production environment. They want to setup a deployment pipeline to do this using Azure DevOps. They know that they should keep their secrets in key vault and they have decided to use the [keyvault configuration builder](https://docs.microsoft.com/en-us/aspnet/config-builder#configuration-builders-in-microsoftconfigurationconfigurationbuilders). The app team doesn't want to use multiple web configs for each environment, but they have separate key vaults for each environment, so they will need to update their web.config file to point to the correct key vault at the time of deployment. 

## Solution
Update the web.config file using the XMLVariableSubstition option of the AzureRMAppDeployTask
TODO: add the steps

Here is the web.config file:

```
<configuration>
  <configSections>
    <section name="configBuilders"
      type="System.Configuration.ConfigurationBuildersSection, System.Configuration, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
      restartOnExternalChanges="false" requirePermission="false"/>
  </configSections>
  <configBuilders>
    <builders>
      <add name="MyKeyVault" vaultName="myazurekv-test-env"
        type="Microsoft.Configuration.ConfigurationBuilders.AzureKeyVaultConfigBuilder, Microsoft.Configuration.ConfigurationBuilders.Azure, Version=1.0.0.0, Culture=neutral" />
    </builders>
  </configBuilders>
  
  <connectionStrings configBuilders="MyKeyVault">
    <add name="ASecretConnectionString" connectionString="PlaceHolder"/>
  </connectionStrings>

  
 <appSettings configBuilders="MyKeyVault">
    <add key="ASecretSetting" value="PlaceHolder"/>
  </appSettings>
```

## References
[https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/transforms-variable-substitution](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/transforms-variable-substitution)
[https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/webapp?view=azure-devops&tabs=windows%2Cyaml#configuration-changes](https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/webapp?view=azure-devops&tabs=windows%2Cyaml#configuration-changes)
