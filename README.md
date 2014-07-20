dashof
======

A simple [pelican](http://getpelican.com) theme. You can see how it looks
like on my website [werthmuller.org](http://werthmuller.org).

The theme has the blog in a subdirectory (/blog), not on the main page.
As of now, it truly is very simple. Many of the features from pelican are
not included, such as the _feed_-possibilities, but also the _tags_-,
_categories_-, _archive_-, and _authors_-pages. It was designed for a single
author page, with a very low-volume blog, so no tagging/categorizing is
required.

It is in many ways more a dirty hack than proper coding to get it to look the
way I want it. (The stuff that follows now could probably be avoided by looking
properly into pelican, and make adjustments were required.)

In oder to make it work, you have to adjust a few things in your `pelicanconf.py`:

1. It requires to know where the blog-directory is:

    :::text
    BLOGDIR = 'blog'

2. You have to insert your blog-directory into the `PAGINATION_PATTERNS`:

    :::text
    PAGINATION_PATTERNS = (
        (1, '{base_name}/index.html', '{base_name}/blog/index.html'),
        (2, '{base_name}/index{number}.html', '{base_name}/blog/index{number}.html'),
        )

3. The blog-name in the static menu must agree with your `BLOGDIR` (the example
   is from my setting):

    :::text
    MENUITEMS = (
           ('Blog', 'blog'),
           ('Research', 'research'),
           ('About', 'about')
           )

4. The contact-page has an additional header, calling the validating java
   script. The template takes your first entry of the `LINKS` as your contact
   page. Otherwise, you have to adjust the `page.html` template.
   But then, you might want to to the contact form completely different anyway.

