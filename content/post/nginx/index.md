---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "nginx reverse proxy with .htaccess"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-06-18T01:38:57+08:00
lastmod: 2020-06-18T01:38:57+08:00
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

## nginx reverse proxy configuration
```
server {
    listen 80;
    server_name _;

    location / {
        include proxy_params;
        proxy_pass http://127.0.0.1:port;
        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/.htpasswd;
    }
}
```

## setup .htaccess

```
sudo apt-get update
sudo apt-get install nginx

# create entry with username
sudo sh -c "echo -n 'yourusername:' >> /etc/nginx/.htpasswd"

# create password
sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"
# https://passwordsgenerator.net/

# view entry
cat /etc/nginx/.htpasswd

sudo vim /etc/nginx/sites-enabled/default
# delete all content and replace with new entry
# sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

sudo service nginx restart

sudo ufw delete allow <port>
```
