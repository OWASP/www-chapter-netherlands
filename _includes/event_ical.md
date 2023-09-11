BEGIN:VEVENT
DTSTAMP:{{ event.date | date: "%Y0101T010000Z" }}
UID:{{ event.date | date: "%Y%m%d" }}-netherlands@owasp.org
ORGANIZER:mailto:netherlands@owasp.org
{%- if event.last-modified %}
LAST-MODIFIED:{{ event.last-modified | date: "%Y%m%dT010000Z" }}
{%- endif %}
{% if event.calendarStart and event.calendarStart != "" -%}
  DTSTART;TZID=Europe/Amsterdam:{{ event.calendarStart }}
{%- else -%}
  DTSTART;TZID=Europe/Amsterdam:{{ event.date | date: "%Y%m%d" }}T
  {%- if event.items.first.start && event.items.first.start != "" -%}
    {{ event.items.first.start | replace: ":", "" }}
  {%- else -%}
    1800
  {%- endif -%}
  00Z
{%- endif %}
{% if event.calendarEnd and event.calendarEnd != "" -%}
  DTEND;TZID=Europe/Amsterdam:{{ event.calendarEnd }}
{%- else -%}
  DTEND;TZID=Europe/Amsterdam:{{ event.date | date: "%Y%m%d" }}T
  {%- if event.items.last.end and event.items.last.end != "" -%}
    {{ event.items.last.end | replace: ":", "" }}
  {%- else -%}
    1800
  {%- endif -%}
  00Z
{%- endif %}
{% if event.calendarTitle and event.calendarTitle != "" -%}
  SUMMARY:{{ event.calendarTitle }}
{%- else -%}
  SUMMARY:OWASP Chapter Netherlands meeting
{%- endif %}
{% assign descriptionString = "DESCRIPTION:" %}
{%- if event.information and event.information != '' %}
  {%- assign descriptionString = descriptionString | append: event.information | append: "\n  
 " %}
{%- endif %}
{%- for item in event.items %}
  {%- assign speakerString = "" %}
  {%- assign speakerSeperator = " by " %}
  {%- for speaker in item.speakers %}
    {%- assign speakerString = speakerString | append: speakerSeperator | append: speaker.name %}
    {%- assign speakerSeperator = " and " %}
  {%- endfor %}
  {%- assign speakerSeperator = " moderated by " %}
  {%- for moderator in item.moderators %}
    {%- assign speakerString = speakerString | append: speakerSeperator | append: moderator.name %}
    {%- assign speakerSeperator = " and " %}
  {%- endfor %}
  {%- if item.start and item.start != '' %}
    {%- assign descriptionString = descriptionString | append: item.start | append: " - " | append: item.end | append: " - " | append: item.title | append: " " | append: speakerString | append: "\n  
 "%}
  {%- endif %}
{%- endfor %}
{%- if event.extraInfo and event.extraInfo != '' %}
  {%- assign descriptionString = descriptionString | append: "\n  
" | append: event.extraInfo | append: "\n  
" %}
{%- endif %}
{%- assign dateForLink = event.date | date: "%B %-d %Y" | replace: " ", "-" | downcase %}
{%- if event.dateString and event.dateString != '' %}
  {%- assign dateForLink =  event.dateString | replace: " ", "-" | downcase %}
{%- endif %}
{%- assign descriptionString = descriptionString | append: "\n  
 " | append: "For more information: https://www.owasp.org/www-chapter-netherlands/allevents#" | append: dateForLink | append: "." %}
{%- assign descriptionString = descriptionString | strip_html | replace: "&#58;",":" %}
{%- assign descriptionLines = descriptionString | split: "\n  
 " %}
{%- assign lineLength =  71 %}
{%- assign newline = "" %}
{%- for descriptionLine in descriptionLines -%}
  {{ newline }}
    {%- assign index = 0 %}
    {%- assign maxIndex = descriptionLine.size | minus: lineLength %}
    {%- for counter in (1..100) %}
      {%- if index < maxIndex  -%}
        {{ descriptionLine | slice: index, lineLength | append: "
 " }}
        {%- assign index = index | plus: lineLength %}
      {%- else -%}
          {%- assign remainingLength = descriptionLine.size | minus: index -%}
          {{ descriptionLine | slice: index, remainingLength }}
          {%- break %}
      {%- endif %}
    {%- endfor %}
  {%- assign newline = "\n
 "%}
{%- endfor %}
END:VEVENT
