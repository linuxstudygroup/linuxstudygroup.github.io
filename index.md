---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<div class="content-list">
{% for cate in site.categories %}
{% capture cate_name %}{{ cate | first }}{% endcapture %}
{% assign sortedPosts = site.categories[cate_name] | sort: 'title'%}
<div class="sub-table {{cate_name}}" style="display: none;">
<h2>{{ cate_name | split: "_" | join: " "}}</h2>
<ul>
{% for post in sortedPosts %}
<li>
<a href="{{ post.url }}">{{ post.title | split: "_" | join: " "}}</a>
</li>
{% endfor %}
</ul>
</div>
{% endfor %}
</div>

<script>
var activate_block = "";

$(document).ready(function(){
    console.log('ready');
    console.log('activate_block: ' + window.activate_block);
    if(window.activate_block == ""){
        console.log("activate_block is empty");
        window.activate_block = $('div.sub-table h2')[0].innerHTML.split(' ').join('_');
        $('div.sub-table.' + window.activate_block)[0].style.display = "";
    }
    var nav_list = $('header nav ul li');
    for(l of nav_list){
        l.onclick = function(){
            var content = this.innerHTML.split(' ').join('_');
            if(content != window.activate_block){
                $('div.sub-table.' + window.activate_block)[0].style.display = "none";
                window.activate_block = content;
                $('div.sub-table.' + window.activate_block)[0].style.display = "";
            }
        }
    }
});
</script>


