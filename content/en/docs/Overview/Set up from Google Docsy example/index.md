---
title: "Set up from Google Docsy example"
linkTitle: "Set up from Google Docsy example"
date: 2021-09-25
categories: ["Examples"]
tags: ["test", "sample", "docs"]
weight: 1
description: >
---

> Origin / 2021-09-25

```bash
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
# need to make default branch from "master" to "main"
mkdir .github && cd .github
mkdir workflows && cd workflows
echo <<< EOL
line 1, ${kernel}
line 2,
line 3, ${distro}
line 4
line ...
EOL > gh-pages2.yml

# github actions yml explaination

## nodjes environment: https://github.com/actions/setup-node



# Set up GitHub Pages: repository -> Settings -> Pages -> select Source to "Branch: gh-pages"


# github
# create shijiansu.github.io.git
git clone https://github.com/shijiansu/shijiansu.github.io
cd shijiansu.github.io
curl https://www.toptal.com/developers/gitignore/api/xcodeinjection,xcode,webstorm+all,vuejs,visualstudiocode,vertx,terraform,swift,sonarqube,scala,react,r,pycharm+all,puppet,objective-c,node,maven,macos,kotlin,jmeter,java,intellij+all,gradle,go,eclipse,androidstudio,android,pydev,python,hugo -o .gitignore
cd ..


# ---

# initiate hugo
hugo new site shijiansu.github.io --force # use force as the folder exists
cd shijiansu.github.io

# ---

# initiate google docsy
# https://www.docsy.dev/docs/getting-started/
sudo npm install -D autoprefixer
sudo npm install -D postcss-cli
sudo npm install -D postcss
## build your own site using the Docsy theme

e

# ---

# set up github action


cd shijian-blog
git submodule add https://github.com/flysnow-org/maupassant-hugo themes/maupassant # will push to github
echo theme = \"maupassant\" >> config.toml

hugo server -D

# deploy to github
## https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action


```

