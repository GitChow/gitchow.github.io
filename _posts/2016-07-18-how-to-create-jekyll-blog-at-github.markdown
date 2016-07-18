---
layout: post
title:  "How to create Jekyll blog and host at Github"
date:   2016-07-18 21:49:15 +0800
categories: jekyll github
tags: [jekyll, github, github-pages, howto]
---

## create a basic site
- create a repo at github, with name $username.github.io `$username` is your github account name
- clone this repo to your local drive, here let's say `D:/$username.github.io`
  - `git clone https://github.com/$username/$username.github.io.git`
- at your local laptop, install Jekyll, `gem install jekyll`
- change directory to `D:`, create jekyll site here: `jekyll new $username.github.io`
- commit, push all the files to remote `https://github.com/$username/$username.github.io.git`
- now you can access https://$username.github.io (in my case: https://gitchow.github.io)

## use tag
> quick way: check directly my commit [add tagging mechanism](https://github.com/GitChow/gitchow.github.io/commit/e6bd205b85f94074c04aef52847cd51838c90890)

1.  create `_data/tags.yml`, it stores the tag names

    ``` yml
    jekyll:
      name: Jekyll
    github:
      name: GitHub
    howto:
      name: HowTo
    ```

2.  create `_layouts/blog_by_tag.html`, it takes care of showing the view of specific tag

    ``` html
    {% raw %}<h1>Articles by tag :{{ page.tag }}</h1>
    <div>
        {% if site.tags[page.tag] %}
            {% for post in site.tags[page.tag] %}
                <a href="{{ post.url }}">{{ post.title }}</a>
            {% endfor %}
        {% else %}
            <p>There are no posts for this tag.</p>
        {% endif %}
    </div>
    ```

3.  in `posts.html` layout, add blow ones

    > please remve below `{% raw %}` tag

    ```liquid
    {% raw %}{% assign post = page %}
    {% if post.tags.size > 0 %}
        {% capture tags_content %}Posted with {% if post.tags.size == 1 %}<i class="fa fa-tag"></i>{% else %}<i class="fa fa-tags"></i>{% endif %}: {% endcapture %}
        {% for post_tag in post.tags %}
              {% assign tag = site.data.tags[post_tag] %}
            {% if tag %}
                {% capture tags_content_temp %}{{ tags_content }}<a href="/blog/tag/{{tag.name}}/">{{ tag.name }}</a>{% if forloop.last == false %}, {% endif %}{% endcapture %}
                {% assign tags_content = tags_content_temp %}
            {% endif %}
        {% endfor %}
    {% else %}
        {% assign tags_content = '' %}
    {% endif %}
    ```

4.  decide where to put below one at `posts.html`

    ``` 
    <p id="post-meta">{{tags_content}}</p>
    ```

5.  crate xxx.md for each tag name, under `blog/tag/`, e.g. `blog/tag/howto.md`, content

    ```md
    ---
    layout: blog_by_tag
    tag: jekyll
    permalink: /blog/tag/Jekyll/
    ---
    ```

6.  finally, use the tag in your post

    ```md
    ---
    layout: post
    title:  "How to create Jekyll blog and host at Github"
    date:   2016-07-18 21:49:15 +0800
    categories: jekyll github
    tags: [jekyll, github, howto]
    ---
    ```



## referrence
- [Jekyll website](https://jekyllrb.com/)
- [Github pages](https://help.github.com/categories/customizing-github-pages/)
- [HOW TO USE TAGS AND CATEGORIES ON GITHUB PAGES WITHOUT PLUGINS](http://www.minddust.com/post/tags-and-categories-on-github-pages/)
- [repo of Róbert Papp](https://github.com/TWiStErRob/twisterrob.github.io/tree/master/_layouts)
