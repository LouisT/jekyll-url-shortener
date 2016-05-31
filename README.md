# URL Shortener
Generates shortened URL pages based on the SHA1 hash of the post date.

Installation
---
Place `url-shortener.rb` in your `_plugins` directory. In your `_config.yml` file
make sure that `safe: false` is set to allow custom plugins.

Post front matter
---
In order for the url shortener to create links you must set `shorten: true` in your post front matter.
The shortened ID is created from the SHA1 of your post date converted to [Unix time].
```yaml
---
  layout:  post
  title:   "URL Shortener for Jekyll."
  date:    1970-01-01 00:00:00           # The timestamp is converted to Unix time.
  shorten: true                          # Shorten this post.
---
```

Post layout
---
In your post layout you can access the generated hash and URL. To display these, place the following anywhere in your `_layouts/post.html` layout.
```
{%if page.short %}Short URL: <a href="{{ page.short.url }}" target="_blank">{{ page.short.hash }}</a>{% endif %}
```

_config.yml
---
In your `_config.yml` file you can set different settings for the URL shortener.
```yaml
shortener:
  basepath: /s/        # Path for stored redirects.
  preserve: false      # Keep previously generated files.
  salt:     "LouisT"   # The optional salt, used when hasing the Unix time.
```

License
---
Copyright (c) 2016, Louis T. ([MIT License]).

[Unix Time]: https://en.wikipedia.org/wiki/Unix_time
[MIT License]: LICENSE
