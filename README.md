# Inroduction
Personal Blog

# Install
- Jekyll
```sh
sudo gem install bundler jekyll
cd <mysite>
bundle install
```

# Run
```sh
jekyll build
jekyll serve # rebuild the site and publish it
bundle exec jekyll serve --incremental
```

when you modify the ``_config.yml``, please run ``jekyll serve``.

When using a Gemfile, you’ll run commands like jekyll serve with bundle exec prefixed. So the full command is:
``bundle exec jekyll serve``

# TODO 
- [ ] bind domain

# Plugin
- [jelyll-toc](https://github.com/toshimaru/jekyll-toc)

    ```markdown
    toc: true
    ```
- jekyll-sitemap

    jekyll-sitemap doesn’t need any setup, it will create your sitemap on build.

- jekyll-feed

    A Jekyll plugin to generate an Atom (RSS-like) feed of your Jekyll posts
- jekyll-seo-tag

    A Jekyll plugin to add metadata tags for search engines and social networks to better index and display your site's content.


# Editor
## Atom
- markdown-writer
    - config file: \_mdwriter.cson

# Reference
- [jekyll](https://jekyllcn.com/)

