---
layout: page
title: Home
id: home
permalink: /
---

<style>
.category-content a {
    text-decoration: none;
    color: #4183c4;
}

.category-content a:hover {
    text-decoration: underline;
    color: #4183c4;
}
</style>

<main>
    {% assign notes = site.notes | sort: 'date' | reverse %}
    {% assign prevdate =  '0000-00-00' %}
    {%- for note in notes -%}
        {% assign date =  note.date | split: ' ' | first %}
        {%- if date != prevdate -%}
            <i>{{date}}</i>:
        {%- endif -%}
        {%- if note.tags contains 'index' -%}
            <li style="padding-bottom: 0.6em; "><a href="{{note.url}}" style="color: #1DA1F2; font-weight:bold">{{ note.title }}</a></li>
        {% else %}
            <li style="padding-bottom: 0.6em; "><a href="{{note.url}}">{{ note.title }}</a></li>
        {%- endif -%}        
        {% assign prevdate =  note.date | split: ' ' | first %}
    {%- endfor -%}
    <br/>
</main>