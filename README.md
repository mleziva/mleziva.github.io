# Starter kit for [Alembic](https://alembic.darn.es/)

This is a very simple starting point if you wish to use Alembic [as a Jekyll theme gem](https://alembic.darn.es/#as-a-jekyll-theme) or as a [GitHub Pages remote theme](https://github.com/daviddarnes/alembic-kit/tree/remote-theme) (see `remote-theme` branch).

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/daviddarnes/alembic-kit)

or

**[Download the GitHub Pages kit](https://github.com/daviddarnes/alembic-kit/archive/remote-theme.zip)**

Add gem "jekyll-remote-theme" to your Gemfile to add the theme as a dependancy
Run the command bundle install in the root of project to install the jekyll remote theme gem as a dependancy
Add jekyll-remote-theme to the list of plugins in your _config.yml file
Add remote_theme: daviddarnes/alembic@main to your _config.yml file to set the site theme
Run bundle exec jekyll serve to build and serve your site
Done! Use the configuration documentation and the example _config.yml file to set things like the navigation, contact form and social sharing buttons

Running locally:
```
bundle install
bundle exec jekyll serve --incremental
```