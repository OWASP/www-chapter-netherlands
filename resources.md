---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="resources" %}

{% assign years = site.data.events | sort %}

| Date               | Name                                                                      | Downloads |
| :----------------- | :-----------------------------------------------------------------------: | -----------------: |

{% for year_hash in years reversed %}

{% assign events = year_hash[1] %}

{% for currentEvent in events %}

{% assign talks = currentEvent[1].items | where: "type", "talk" %}

{% for item in talks %}

| currentEvent[1].date | item.title | &nbsp; |

{% endfor %}

{% endfor %}

{% endfor %}

| June 16 2022       | Staying In Control Of Your Cloud Application Landscape by Priyam Awasthy and Spandan Chandra | [Recording](https://youtu.be/r1-ID0z3rBY) |
|                    | OWASP Cloud-Native Application Security Top 10 by Filip Chyla                                | [Recording](https://youtu.be/4qr7eqBqS58) |
