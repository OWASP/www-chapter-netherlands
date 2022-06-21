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

{% assign yearLinks = year %}

{% else %}

{% assign yearLinks = yearLinks | append: ' &nbsp;&#124;&nbsp; ' | append: year %}

{% endif %}

{% endfor %}

{% for year_hash in years reversed %}

{% assign year = year_hash[0] %}

## {{ year }}

{% endfor %}

{% assign events = site.data.events.2022 | sort: 'date' %}

{% for event in events %}

{{event.date | date: "%-d %B %Y"}}

{% endfor %}
