---
title: Publications
layout: publications
description: Publications
permalink: "/publications"
intro_image: "images/illustrations/robot-journal.png"
intro_image_absolute: true
intro_image_hide_on_mobile: false
---

<div id="filter_by" class="filter_by"></div>
<ul id="pub_list"></ul>


<script>
    var url_tag = new URLSearchParams(window.location.search).get("t");
    var div = document.getElementById("filter_by");
    var ul = document.getElementById("pub_list");
    if (url_tag != null) {
        div.innerText = "Publications with the " + url_tag + " tag";
    }
    else {
        div.style.display = "none";
    }
    {% assign publications = site.publications| sort: 'date' | reverse %}
    {% for post in publications %}
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
            <div class="pub-strip">
                <b class="post_title">
                    {{ post.title }},
                </b>
                <i class="post_authors">
                    {{ post.authors }},
                </i>
                <i class="post_extras">
                    {{ post.extras}}
                </i>
                <hr class="separator">
                <p class="post_abstract">
                    {{ post.content}}
                </p>
            {% for tag in post.tags %}
                &#9839;<a href="?t={{ tag }}" class="post_tag">
                {{ tag }} 
            </a>
            {% endfor %}
            {% if post.external_url != nil %}
                <br>
                <a href="{{ post.external_url }}" class="external_link" target="_blank">External Link</a>
            {% endif %}
            </div>`;
            ul.appendChild(li);
        }
    {% endfor %}
</script>

