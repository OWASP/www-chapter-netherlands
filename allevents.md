---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="allevents" %} 

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

## {{ year_hash[0] }}

{% assign events = year_hash[1] | sort %}

{% assign eventLinks = "" %}

{% for currentEvent in events reversed %}

{% assign event = currentEvent[1] %}

{% assign eventDateString = event.date | date: "%B %-d %Y" %}
{% if event.dateString and event.dateString != '' %}{% assign eventDateString = event.dateString %}{% endif %}

{% assign eventDateUrl = eventDateString | replace: " ", "-" | downcase %}

{% if eventLinks == "" %}

{% assign eventLinks = '[' | append: eventDateString | append: '](#' | append: eventDateUrl | append: ')' %}

{% else %}

{% assign eventLinks = eventLinks | append: ' &nbsp;&#124;&nbsp; ' | append: '[' | append: eventDateString | append: '](#' | append: eventDateUrl | append: ')' %}

{% endif %}

{% endfor %}

{{ eventLinks }}

{% for currentEvent in events reversed%}

{% assign event = currentEvent[1] %}  
{% include event.md %}

{% endfor %}

{% endfor %}
