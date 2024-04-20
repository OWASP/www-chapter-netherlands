---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="upcomingevents" %} 

{% assign years = site.data.events | sort %}

{% for year_hash in years reversed %}

{% assign events = year_hash[1] %}

{% for currentEvent in events %}

{% capture nowunix %}{{'now' | date: '%Y%m%d'}}{% endcapture %}
{% capture eventdate %}{{currentEvent[1].date | date: '%Y%m%d'}}{% endcapture %}

{% if eventdate >= nowunix %} 

{% assign event = currentEvent[1] %}  
{% include event.md %}

{% endif %}

{% endfor %}

{% endfor %}
