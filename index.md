---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<ul class="page-list">
{% for cate in site.categories %}
{% capture cate_name %}{{ cate | first }}{% endcapture %}
{% assign sortedPosts = site.categories[cate_name] | sort: 'title'%}
    <li>
        <div class="sub-table">
        <h2>{{ cate_name | split: "_" | join: " "}}</h2>
        <ul>
            {% for post in sortedPosts %}
            <li>
                <a href="{{ post.url }}">{{ post.title | split: "_" | join: " "}}</a>
            </li>
            {% endfor %}
        </ul>
        </div>
    </li>
{% endfor %}
</ul>


