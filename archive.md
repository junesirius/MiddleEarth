---
layout: default
title: 标签
---

<div class="well article">
{% assign sortedcategories = site.categories | sort %}
{% for category in sortedcategories %}
    <a id="{{ category[0] }}" style="position: relative; top: -50px"></a>
    <h2><a href="{{ site.baseurl }}/categories#{{ category[0] }}">{{ category[0] }}</a></h2>
    <ul>
        {% assign pages_list = category[1] %}
        {% for node in pages_list reversed %}
            {% if node.title != null %}
            {% if group == null or group == node.group %}
                <li>
                    <div style="margin: 0; padding: 0">
                        <a href="{{ site.baseurl}}{{ node.url }}"> {{ node.title }}</a>
                    </div>
                </li>
            {% endif %}
            {% endif %}
        {% endfor %}
        {% assign pages_list = nil %}
    </ul>
{% endfor %}    
</div>
