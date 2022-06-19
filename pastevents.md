---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="pastevents" %} 

{% assign events = site.data.events.2022 | sort: 'date' %}

{% for event in events %}
{{event.date}}
{% endfor %}
