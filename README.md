# austinmleziva.com

Personal portfolio and blog, built with [Jekyll](https://jekyllrb.com/) and the [Chirpy][chirpy] theme and deployed to
GitHub Pages by `.github/workflows/pages-deploy.yml` on every push to `master`.

## Running locally

### Prerequisites

- **Ruby 3.3 or later** (CI uses 3.3).
  - Windows: install [RubyInstaller](https://rubyinstaller.org/downloads/) **with Devkit**, and let it run
    `ridk install` at the end of setup.
  - macOS/Linux: install Ruby with your package manager or a version manager such as `rbenv`.
- **Bundler:** `gem install bundler`

Alternatively, open the repository in the included dev container (`.devcontainer/`), which has Ruby preinstalled.

### Install dependencies

```shell
bundle install
```

### Preview the site

```shell
bundle exec jekyll serve --livereload
```

Open <http://127.0.0.1:4000>. The page reloads automatically when you save a file. Changes to `_config.yml` require
restarting the server. Add `--drafts` to also show posts in `_drafts/`.

On macOS/Linux you can also run `bash tools/run.sh`.

### Production build and link check

This is what CI runs before deploying:

```shell
JEKYLL_ENV=production bundle exec jekyll build
bundle exec htmlproofer _site --disable-external --ignore-urls "/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/,/^http:\/\/localhost/"
```

`htmlproofer` needs the `libcurl` library, which Windows doesn't include, so on Windows run the link check in the dev
container or rely on CI.

## Writing posts

Posts live in `_posts/<category>/YYYY-MM-DD-title.md`. Each new post goes on its own branch and is merged to `master`
through a pull request. See the [Chirpy writing guide](https://chirpy.cotes.page/posts/write-a-new-post/) for front
matter options and formatting.

---

# Chirpy Starter

[![Gem Version](https://img.shields.io/gem/v/jekyll-theme-chirpy)][gem]&nbsp;
[![GitHub license](https://img.shields.io/github/license/cotes2020/chirpy-starter.svg?color=blue)][mit]

When installing the [**Chirpy**][chirpy] theme through [RubyGems.org][gem], Jekyll can only read files in the folders
`_data`, `_layouts`, `_includes`, `_sass` and `assets`, as well as a small part of options of the `_config.yml` file
from the theme's gem. If you have ever installed this theme gem, you can use the command
`bundle info --path jekyll-theme-chirpy` to locate these files.

The Jekyll team claims that this is to leave the ball in the user’s court, but this also results in users not being
able to enjoy the out-of-the-box experience when using feature-rich themes.

To fully use all the features of **Chirpy**, you need to copy the other critical files from the theme's gem to your
Jekyll site. The following is a list of targets:

```shell
.
├── _config.yml
├── _plugins
├── _tabs
└── index.html
```

To save you time, and also in case you lose some files while copying, we extract those files/configurations of the
latest version of the **Chirpy** theme and the [CD][CD] workflow to here, so that you can start writing in minutes.

## Usage

Check out the [theme's docs](https://github.com/cotes2020/jekyll-theme-chirpy/wiki).

## Contributing

This repository is automatically updated with new releases from the theme repository. If you encounter any issues or want to contribute to its improvement, please visit the [theme repository][chirpy] to provide feedback.

## License

This work is published under [MIT][mit] License.

[gem]: https://rubygems.org/gems/jekyll-theme-chirpy
[chirpy]: https://github.com/cotes2020/jekyll-theme-chirpy/
[CD]: https://en.wikipedia.org/wiki/Continuous_deployment
[mit]: https://github.com/cotes2020/chirpy-starter/blob/master/LICENSE
