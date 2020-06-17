---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Hugo Setup"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-06-14T23:52:28+08:00
lastmod: 2020-06-14T23:52:28+08:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---


## Install hugo on mac

Use the script from https://rimdev.io/hugo-extended-latest-install-script-for-macos/ to install hugo.


## Setup repo

Follow the official guide https://sourcethemes.com/academic/docs/deployment/#github-pages to fork the Academic Kickstart repository.

## Configure your site

```
git add .
git commit -m "Initial commit"
git push -u origin master
```

## publish to github pages

create new post using `hugo new  --kind post post/hugo`

publish/update github pages
```
hugo
cd public
git add .
git commit -m "Build website"
git push origin master
cd ..
```