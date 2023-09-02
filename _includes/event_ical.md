BEGIN:VEVENT
DTSTAMP:{{ event.date | date: "%Y0101T010001Z" }}
UID:{{ event.date | date: "%Y%m%d" }}-netherlands@owasp.org
ORGANIZER:mailto:netherlands@owasp.org
DTSTART;TZID=Europe/Amsterdam:{{ event.date | date: "%Y%m%d" }}T
{%- if event.items.first.start && event.items.first.start != "" -%}
  {{ event.items.first.start | replace: ":", "" }}
{%- else -%}
  1800
{%- endif -%}
00Z
DTEND;TZID=Europe/Amsterdam:{{ event.date | date: "%Y%m%d" }}T
{%- if event.items.last.end && event.items.last.end != "" -%}
  {{ event.items.last.end | replace: ":", "" }}
{%- else -%}
  1800
{%- endif -%}
00Z
SUMMARY:OWASP Chapter Netherlands meeting
END:VEVENT
