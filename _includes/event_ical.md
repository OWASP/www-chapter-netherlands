BEGIN:VEVENT 
DTSTAMP:{{ event.date | date: "%Y0101T010000Z" }}
UID:{{ event.date | date: "%Y%m%-d" }}-netherlands@owasp.org
ORGANIZER:mailto:netherlands@owasp.org
DTSTART:{{ event.date | date: "%Y%m%-d" }}T{{ event.items.first.start | replace: ":", "" }}00Z
DTEND:{{ event.date | date: "%Y%m%-d" }}T{{ event.items.last.end | replace: ":", "" }}00Z
{% if event.tileString and event.tileString != '' %}SUMMARY:{{ event.tileString }}
{% else %}SUMMARY:{{ event.date | date: "%B %-d %Y" }} OWASP Chapter Netherlands meeting{% endif %}
{% if event.location and event.location != '' %}LOCATION: {{ event.location }} {% endif %}
DESCRIPTION:{% if event.information and event.information != '' %}{{ event.information  | strip_html }}\n
\n
{% endif %}{% for item in event.items %}{% assign speakerString = "" %}{% assign speakerSeperator = " by " %}{% for speaker in item.speakers %}{% assign speakerString = speakerString | append: speakerSeperator | append: speaker.name %}{% assign speakerSeperator = " and " %}{% endfor %}{% assign speakerSeperator = " moderated by " %}  {% for moderator in item.moderators %}{% assign speakerString = speakerString | append: speakerSeperator | append: moderator.name %}{% assign speakerSeperator = " and " %}{% endfor %}{% if item.start and item.start != '' %}{{ item.start }} - {{ item.end }} - {{ item.title }} {{ speakerString }}\n
{% endif %}{% endfor %}\n
{% if event.extraInfo and event.extraInfo != '' %}{{ event.extraInfo | strip_html }}\n
\n
{% endif %}For more information:  https://www.owasp.org/www-chapter-netherlands/allevents/#{{ event.date | date: "%B %-d %Y"}} .
END:VEVENT
