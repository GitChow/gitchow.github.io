## [The home page](https://jekyllrb.com/docs/frontmatter/)

## what is JekyII
>Jekyll is a simple, blog-aware, static site generator.
It takes a template directory containing raw text files in various formats, runs it through a converter (like Markdown) and our Liquid renderer, and spits out a complete, ready-to-publish static website suitable for serving with your favorite web server.

>Jekyll is, at its core, a text transformation engine. 

- JekyII: the engin behind GitHub Pages

## quick start
``` ruby
~ $ gem install jekyll
~ $ jekyll new myblog
~ $ cd myblog
~/myblog $ jekyll serve
# => Now browse to http://localhost:4000
```

## installation
### requirements
- ruby
- RubyGem (the ruby package manager)
> run JekyII on Windows is not offically supported.
tip for installation in windwows [Link](https://jekyllrb.com/docs/windows/#installation)

## directory srtucture
[refer to this](https://jekyllrb.com/docs/structure/)

## confugration
[refer to this](https://jekyllrb.com/docs/configuration/)

## writeing post
> posts are stored as files, rather than in database

> `_posts` folder is where blog posts will live

- naming convention for file created under `_posts`: `YEAR-MONTH-DAY-title.MARKUP`, e.g.
  - 2011-12-31-new-years-eve-is-awesome.md
  - 2012-09-12-how-to-write-a-blog.textile
- all blog post file must begin with `YAML Front Matter`

### include images and resources
```
![My helpful screenshot]({{ site.url }}/assets/screenshot.jpg)
... you can [get the PDF]({{ site.url }}/assets/mydoc.pdf) directly.
```

### index of posts
```
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```

## working with drafts
> `_drafts` folder

## creating pages
[refer to this page](https://jekyllrb.com/docs/pages/)