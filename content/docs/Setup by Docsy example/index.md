---
title: "Setup by Docsy example"
categories: ["Examples"]
tags: ["test", "sample", "docs"]
weight: 9999
description: >
---

> Su Shijian / 2021-09-25

```bash
# about google docsy - https://www.docsy.dev/docs/

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

# github actions yml explaination
## hugo github action:
## https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action
## nodjes environment: https://github.com/actions/setup-node

# github pages
## set up GitHub Pages:
## repository -> Settings -> Pages -> select Source to "Branch: gh-pages"
```
