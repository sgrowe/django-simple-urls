# django-simple-urls
Readable and maintainable django urls

When defining your Django app’s urls, regexes with named arguments are a very powerful and flexible solution, but they’re *so* ugly! The fact that they are awkward to write and tricky to read makes creating and maintaining your `urls.py` more of a pain than it needs to be.


`django-simple-urls` provides a straightforward syntax which is readable at a glance and easy to remember. It provides an alternative to django’s built-in `url` function: `simple_url`. The two can be mixed-and-matched as you please so you can use `simple_url`s most of the time whilst still being free to fallback to regexes if needs be.


Here’s an example of how `simple_url`s can make a grotesque `urls.py` much more beautiful.

    # before:

    from django.conf.urls import url

    url(r'^article/(?P<article_id>\d+)/(?P<article_slug>[^/]+)$', views.article)

    # after:

    from django_simple_urls import simple_url as url

    simple_url('/article/ article_id: int / article_slug ', view.article)



Using named groups in your django project's `urls.py` is the most flexible way to wire up your urls to your views.
But the urls are *so* ugly! For example, rather than writing this grotesque regex

    url(r'^article/(?P<article_id>\d+)/(?P<article_slug>[^/]+)$', views.article)

You can instead write the much more readable

    simple_url('/article/ article_id: int / article_slug ', view.article)



## Type specifiers


- *blank* - one or more characters, excluding forward slashes
- `int` - one or more numeric digits
- `alpha` - one or more alphabetical letters, upper or lower case
- `multi` - one or more characters, including forward slashes
