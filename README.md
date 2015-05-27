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

    ```
    BLOGDIR = 'blog'
    ```

2. Blog-directory

  1. Pelican 3.3.0: You have to insert your blog-directory into the `PAGINATION_PATTERNS`:

      ```
      PAGINATION_PATTERNS = (
          (1, '{base_name}/index.html', '{base_name}/blog/index.html'),
          (2, '{base_name}/index{number}.html', '{base_name}/blog/index{number}.html'),
          )
      ```
  2. Pelican 3.5.0: You have to insert your blog-directory into the `INDEX_SAVE_AS`:

      ```
      INDEX_SAVE_AS = 'blog/index.html'
      ```

3. The blog-name in the static menu must agree with your `BLOGDIR` (the example
   is from my setting):

    ```
    MENUITEMS = (
           ('Blog', 'blog'),
           ('Research', 'research'),
           ('About', 'about')
           )
    ```

4. The footer is defined in its own tag as a string:

    ```
    FOOTER = 'My Site ~ 2014 Example Author'
    ```

5. The contact-page has an additional header, calling the validating java
   script. The template takes your first entry of the `LINKS` as your contact
   page. Otherwise, you have to adjust the `page.html` template.
   But then, you might want to do the contact form completely different anyway.

6. For the inclusion of IPython notebooks, you need my modified version of the
   [`liquid_tags`](https://github.com/prisae/pelican-plugins/blob/master/liquid_tags/notebook.py)
    plugin for pelican, and provide the required parameters (I also use the
    `neighbors` plugin in the article-template):

    ```
    PLUGIN_PATH = '/path/to/your/plugins'
    PLUGINS = ['liquid_tags.notebook', 'neighbors']
    NOTEBOOK_DIR = '/path/to/your/notebooks/relative/to/blog/path'
    ```

The modified plugin `liquid_tags` will create the following files:

* `output/theme/static/css/ipynb.css`
* `output/theme/static/js/collapse.js`
* `output/theme/static/js/math.js`


The following files are not provided by this theme itself:

* `dashof/static/css/normalize.css`
* `dashof/static/css/pygment.css`
* `dashof/static/js/gen_validatorv4.js`

The file `normalize.css` is from [git.io/normalize](http://git.io/normalize).

The file `gen_validatorv4.js` is from
[javascript-coder.com](http://www.javascript-coder.com/html-form/javascript-form-validation.phtml).

The file `pygment.css` was created with

    $ pygmentize -S default -f html > dashof/static/css/pygment.css


