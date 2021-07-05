---
layout: default
title: 词表
---
<!-- Look for the name list of all glossaries -->
{% assign glossary_list = "" | split: "" %}
{% for node in site.posts %}
    {% for glossary in node.glossaries %}
        {% unless glossary_list contains glossary %}
            {% assign glossary_list = glossary_list | push: glossary %}
        {% endunless %}
    {% endfor %}
{% endfor %}

<!-- Begin display-->
<div class="well article">
{% assign sortedglossaries = glossary_list | sort %}
{% for glossary in sortedglossaries %}
    <a id="{{ glossary }}" style="position: relative; top: -50px"></a>
    <h2>{{ glossary }}</h2>
    <ul>
        {% for node in site.posts %}
            {% for post_glossary in node.glossaries %}
                {% if post_glossary == glossary and node.title != null%}
                    <li>
                        <div style="margin: 0; padding: 0">
                            <a href="{{ site.baseurl}}{{ node.url }}"> {{ node.title }}</a>
                        </div>
                    </li>
                    {% break %}
                {% endif %}
            {% endfor %}
        {% endfor %}
    </ul>
{% endfor %}    
</div>
