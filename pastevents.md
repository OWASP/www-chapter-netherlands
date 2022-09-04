---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="pastevents" %} 

{% assign years = site.data.events | sort %}

{% assign yearLinks = "" %}

{% for year_hash in years reversed %}

{% assign year = year_hash[0] %}

{% if yearLinks == "" %}

{% assign yearLinks = '[' | append: year | append: '](#' | append: year | append: ')' %}

{% else %}

{% assign yearLinks = yearLinks | append: ' &nbsp;&#124;&nbsp; ' | append: '[' | append: year | append: '](#' | append: year | append: ')' %}

{% endif %}

{% endfor %}

{{ yearLinks }}

{% for year_hash in years reversed %}

## {{ year }}

{% assign events = year_hash[1] %}

{{ events | inspect }}

{% for currentEvent in events reversed %}

{% assign event = currentEvent[1] %}
{% include event.md %}

{% endfor %}

{% endfor %}
