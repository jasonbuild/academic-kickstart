---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Multi-threaded Python Parallelization"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-06-14T23:46:21+08:00
lastmod: 2020-06-14T23:46:21+08:00
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

One common use case of parallel in Python is network requests. One of the most simple solutions to send million of requests is using `multiprocessing.dummy.Pool`.

Sample code

```python
import requests
from multiprocessing.dummy import Pool as ThreadPool


def fetch(url):
  resp = requests.get(url)
  if resp.status_code == 200:
    content = resp.text
  else:
    content = None
  data = {
    'url': url,
    'content': content
  }
  return data


urls = [
  ...
]

pool = ThreadPool(4)
data_list = pool.map(requests.get, urls)
pool.close()
pool.join()
```