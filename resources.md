---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="resources" %}

{% assign years = site.data.events | sort %}

<table>  
  <thead>
    <tr>
      <th style="text-align: left">Date</th>
      <th style="text-align: center">Name</th>
      <th style="text-align: right">Presentation Link</th>
    </tr>
  </thead>
  <tbody>
{% for year_hash in years reversed %}
{% assign events = year_hash[1] | sort %}
{% for currentEvent in events reversed %}
{% assign talks = currentEvent[1].items | where_exp: "item", "item.type == 'talk'" %}
{% assign dateString = currentEvent[1].date | date: "%B %-d %Y" %}
{% for item in talks %}
    {% assign itemHasResources = false %}
    {% if item.presentationUrl and item.presentationUrl != '' %}
    {% assign itemHasResources = true %}
    {% endif %}
    {% if item.youtubeUrl and item.youtubeUrl != '' %}
    {% assign itemHasResources = true %}
    {% endif %}
    {% if itemHasResources %}
    {% assign speakerString = "" %}
    {% assign speakerSeperator = "by " %}
    {% for speaker in item.speakers %}
    {% assign speakerString = speakerString | append: speakerSeperator | append: '<i>' | append: speaker.name | append: '</i>' %}
    {% assign speakerSeperator = " and " %}
    {% endfor %}
    <tr>
      <td style="text-align: left">{{ dateString }}</td>
      <td style="text-align: center">{{item.title }}<br />{{ speakerString }}</td>
      <td style="text-align: right">
        {% if item.presentationUrl and item.presentationUrl != '' %}<a href="{{ item.presentationUrl }}">Presentation</a>{% endif %}
        {% if item.presentationUrl and item.presentationUrl != ''and  item.youtubeUrl and item.youtubeUrl != '' %}<br />{% endif %}
        {% if item.youtubeUrl and item.youtubeUrl != '' %}<a href="{{ item.youtubeUrl }}">Recording</a>{% endif %}
      </td>
    </tr>
    {% assign dateString = '&nbsp;' %}
    {% endif %}
{% endfor %}
{% endfor %}
{% endfor %}
  </tbody>
</table>
