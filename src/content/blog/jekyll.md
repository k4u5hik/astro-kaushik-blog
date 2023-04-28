---
author: Kaushik Chemburkar
pubDatetime: 2023-02-25T09:02:01+11:00
title: Jekyll - Clean installation
postSlug: jekyll
featured: false
draft: false
tags:
  - jekyll
ogImage: ""
description:
  How to do a clean Jekyll installation and host it on Github.
---

## How to host a Jekyll blog on Github

The following information and more details can be found on [https://jekyllrb.com/docs/](https://jekyllrb.com/docs/)

- Go to github.com and create a new repository with your own github username.
- name it as `username.github.io`
- Add a readme file.
- Open vscode. Go to your folder where you want to create the site.

```bash
git clone REPOSITORY_URL
```

- Open the folder in vscode

```bash
gem install bundler jekyll
```

```bash
jekyll new username.github.io --force
```

```bash
cd username.github.io
```

- Edit **`_config.yml`** file. Replace with your details

```yaml
title: Kaushik Chemburkar
email: attherate@gmail.com
description: >- # this means to ignore newlines until "baseurl:"
  Notes for myself
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: _Kaushik
github_username:  k4u5hik
mastodon:
  - username: kaushikc
    instance: mastodon.social

# Build settings
theme: minima
plugins:
  - jekyll-feed
```

- Append the following to the `Gemfile`

```ruby
# install jekyll-admin
gem 'jekyll-admin', group: :jekyll_plugins
```

- Sass deprecation warnings were disabled by appending the following to the `Gemfile` ([Optional](https://github.com/jekyll/minima/issues/709))

```ruby
sass:
  quiet_deps: true
```

- Run the following commands on the terminal

```bash
bundle install
```

```bash
bundle exec jekyll serve
```

- Open `http://localhost:4000/` in your browser
- Open `http://localhost:4000/admin/` in your browser
- If everything is fine, commit and push the changes to github

```bash
git add .
git commit -m "Jekyll clean install"
git push
```

That's all! Your site is live at `https://username.github.io`
