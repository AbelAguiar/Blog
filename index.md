---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<div class="row">
    <div class="col-lg-8 col-md-10 mx-auto">
        {% for post in site.posts %}
        <div class="post-preview">
            <a href="{{ post.url }}">
                <h2 class="post-title">
                    {{ post.title }}
                </h2>
                <h3 class="post-subtitle">
                    {% if post.description %}{{ post.description  | strip_html | strip_newlines | truncate: 60 }}{% else %}{{ post.content | strip_html | strip_newlines | truncate: 60 }}{% endif %}
                </h3>
            </a>
            <p class="post-meta">
                Postado por: **{{ post.author }}** | {{ post.date }}
            </p>
        </div>
        <hr>
        {% endfor %}
    </div>
</div>
