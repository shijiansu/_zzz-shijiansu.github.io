---
date: 2021-09-25
author: Su Shijian
title: "Setup by Docsy example"
tags: ["TBD"]
categories: ["TBD"]
description: >
---

> Su Shijian | 2021-09-25

## Environment

- Nodejs v16.10.0
- Hugo v0.88.1 - Websites builder
- Google Docsy theme (via Docsy example) - theme/docsy
  - SCSS
  - https://www.docsy.dev/
  - https://www.docsy.dev/docs/adding-content/content/ (Userful for customization!)
- GitHub Actions - .github/workflows
- GitHub Pages

## Steps

```bash
# about google docsy theme - https://www.docsy.dev/docs/

# google docsy example template
# create the github repository from the google docsy example "Use this template"
# refer to https://www.docsy.dev/docs/getting-started/#using-the-github-ui

# github hosting
# make it possible hosting in the github: <user>.github.io
# refer to
## https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
## https://docs.github.com/en/pages/getting-started-with-github-pages

# development environment
brew -v # Homebrew 3.2.13
nvm --version # 0.35.3, install via brew
node -v # v16.10.0 # install via nvm
# nvm install node --reinstall-packages-from=node # if need to upgrade
brew install hugo # default is with "extended" for scss
hugo version # hugo v0.88.1+extended

# github
# include public, resources in .gitignore
# refer to https://www.toptal.com/developers/gitignore/api/hugo

# clean up the google docsy example
rm deploy.sh
rm CONTRIBUTING.md
rm LICENSE
rm Dockerfile
rm docker-compose.yaml
rm netlify.toml

# verify
## important
## in google docsy, it requires hugo extended for scss
git clone https://github.com/shijiansu/shijiansu.github.io
cd shijiansu.github.io
git submodule update --init --recursive --depth 1 # because themes/docsy is submodule
# below are also the submodule, please ensure they exists in your local
## themes/docsy/assets/vendor/Font-Awesome
## themes/docsy/assets/vendor/bootstrap
# if you do not set up from the google docsy example, 
# then you need to install below nodejs dependencies manually
npm install -D autoprefixer
npm install -D postcss-cli
npm install -D postcss
npm install

hugo server

# github actions
# https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action
# make default branch from "master" (as google docsy example) to "main" because of gh-pages.yml
mkdir .github && cd .github
mkdir workflows && cd workflows
echo <<< EOL
line ...
EOL > gh-pages.yml

# github actions yml explanation
# this is check in to repository "gh-pages" branch,
# which will setup in github pages as source of github pages.
## hugo github action:
## https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action
## nodjes environment: https://github.com/actions/setup-node

# github pages
## set up GitHub Pages:
## repository -> Settings -> Pages -> select Source to "Branch: gh-pages"
```

## Reference

- https://github.com/google/docsy/blob/master/userguide/content/en/_index.html
- https://github.com/google/docsy-example
