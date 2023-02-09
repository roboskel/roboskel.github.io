---
layout: news
title: "News"
intro_image: "images/illustrations/robot_news.png"
intro_image_absolute: true
intro_image_hide_on_mobile: false
---
<div id="filter_by" class="filter_by"></div>
<ul id="news_list"></ul>


<script>
    var url_tag = new URLSearchParams(window.location.search).get("t");
    var div = document.getElementById("filter_by");
    var ul = document.getElementById("news_list");
    if (url_tag != null) {
        div.innerText = "Posts with the " + url_tag + " tag";
    }
    else {
        div.style.display = "none";
    }
    {% for post in site.posts %}
        var has_tag = false;
        {% for tag in post.tags %}
            if (url_tag == null || "{{ tag }}" == url_tag) {
                has_tag = true;
                // There should be a {\% break \%} here, but it... breaks js
            }
        {% endfor %}
        if (has_tag) {
            var li = document.createElement("li");
            li.innerHTML = `
            <div class="news-strip">
                <a href="{{ post.url }}" class="post_title">
                {{ post.title }}
            </a>
            <br>
            {% for tag in post.tags %}
                &#9839;<a href="?t={{ tag }}" class="post_tag">
                {{ tag }}
            </a>
            {% endfor %}
            {{ post.excerpt}}
            </div>`;
            ul.appendChild(li);
        }
    {% endfor %}
</script>

