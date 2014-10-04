m.py
====

Takes an HTML document, minifies and inlines all CSS and JS. Includes WSGI middleware for platforms like Google AppEngine, and optional memcached caching.

Installation
-------------

Add m.py to your project, as well as all the dependencies;
 - cssutils
 - htmlmin
 - slimit (JS minifier)
 - BeautifulSoup4

Usage
--------

```python
from m import minify
minified_html = minify(html)
```

__On AppEngine__:

Replace:
```python
app = webapp2.WSGIApplication([
    ('/', MainHandler),
])
```
with:
```python
app = webapp2.WSGIApplication([
    ('/', MainHandler),
])
import m
app = m.WSGIMiddleware(app, memcache=memcache)
```

