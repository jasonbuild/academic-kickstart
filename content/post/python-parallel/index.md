---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Python Parallel"
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


## multithread
```python
import urllib2
from multiprocessing.dummy import Pool as ThreadPool

urls = [
  'http://www.python.org',
  'http://www.python.org/about/',
  'http://www.onlamp.com/pub/a/python/2003/04/17/metaclasses.html',
  'http://www.python.org/doc/',
  'http://www.python.org/download/',
  'http://www.python.org/getit/',
  'http://www.python.org/community/',
  'https://wiki.python.org/moin/',
  'http://planet.python.org/',
  'https://wiki.python.org/moin/LocalUserGroups',
  'http://www.python.org/psf/',
  'http://docs.python.org/devguide/',
  'http://www.python.org/community/awards/'
  # etc..
  ]

# Make the Pool of workers
pool = ThreadPool(4)
# Open the urls in their own threads
# and return the results
results = pool.map(urllib2.urlopen, urls)
#close the pool and wait for the work to finish
pool.close()
pool.join()
```

## multiprocess
```python
from multiprocessing import Pool
from PIL import Image

SIZE = (75,75)
SAVE_DIRECTORY = 'thumbs'

def get_image_paths(folder):
  return (os.path.join(folder, f)
      for f in os.listdir(folder)
      if 'jpeg' in f)

def create_thumbnail(filename):
  im = Image.open(filename)
  im.thumbnail(SIZE, Image.ANTIALIAS)
  base, fname = os.path.split(filename)
  save_path = os.path.join(base, SAVE_DIRECTORY, fname)
  im.save(save_path)

if __name__ == '__main__':
  folder = os.path.abspath(
    '11_18_2013_R000_IQM_Big_Sur_Mon__e10d1958e7b766c3e840')
  os.mkdir(os.path.join(folder, SAVE_DIRECTORY))

  images = get_image_paths(folder)

  pool = Pool()
    pool.map(create_thumbnail, images)
    pool.close()
    pool.join()

```