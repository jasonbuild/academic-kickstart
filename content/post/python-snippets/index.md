---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Python Snippets"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-06-21T15:04:23+08:00
lastmod: 2020-06-21T15:04:23+08:00
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

# general
## split a list into evenly sized chunks

```python
def chunks(l, n):
    n = max(1, n)
    return (l[i:i + n] for i in range(0, len(l), n))

items = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
bin_size = 3
for chunk_ind, chunk_items in enumerate(chunks(items, bin_size)):
    print('{}\t{}'.format(chunk_ind, chunk_items))
```


# csv
## list of dicts to csv

```python
import csv

items_list = [
    {'name':'bob', 'age':25, 'weight':200},
    {'name':'jim', 'age':31, 'weight':180}
]
keys = items_list[0].keys()
with open('items_list.csv', 'w') as output_file:
    dict_writer = csv.DictWriter(output_file, keys)
    dict_writer.writeheader()
    dict_writer.writerows(items_list)
```