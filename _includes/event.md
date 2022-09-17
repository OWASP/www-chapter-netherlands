{% if event.dateString and event.dateString != '' and event.tileString and event.tileString != '' %}
<h3 id="{{ event.dateString | replace: " ", "-" | downcase }}">{{ event.titleString }}</h3>
{% elsif event.dateString and event.dateString != '' %}
<h3 id="{{ event.dateString | replace: " ", "-" | downcase }}">{{ event.dateString }}</h3>
{% elsif event.tileString and event.tileString != '' %}
<h3 id="{{ event.date | date: "%B %-d %Y" | replace: " ", "-" | downcase }}">{{ event.titleString }}</h3>
{% else %}
### {{ event.date | date: "%B %-d %Y"}}
{% endif %}
{{ event.information }}  

{% if event.location and event.location != '' %}Location: {{ event.location }}  {% endif %}
{% if event.address and event.address != '' %}Address: {{ event.address }}  {% endif %}
{% if event.locationUrl and event.locationUrl != '' %}Link: [{{ event.locationUrl }}]({{ event.locationUrl }})  {% endif %}
{% if event.meetupUrl and event.meetupUrl != '' %}  
Please register via: [{{ event.meetupUrl }}]({{ event.meetupUrl }})  {% endif %}

{% for item in event.items %}
{% assign speakerString = "" %}
{% assign speakerSeperator = "by " %}
{% for speaker in item.speakers %}
{% assign speakerString = speakerString | append: speakerSeperator | append: '<strong>' | append: speaker.name | append: '</strong>' %}
{% assign speakerSeperator = " and " %}
{% endfor %}
{% if item.start and item.start != '' %}{{ item.start }} - {{ item.end }} - **{{ item.title }}**{{ speakerString }}  
{% endif %}{% endfor %} 

{% if event.extraInfo and event.extraInfo != '' %}{{ event.extraInfo }}{% endif %}

{% assign talks = event.items | where: "type", "talk" %}  

{% for item in talks %} 
#### {{ item.title }}
{% if item.presentationUrl and item.presentationUrl != '' %}[Download the presentation]({{ item.presentationUrl }})  {% endif %}
{% if item.youtubeUrl and item.youtubeUrl != '' %}[Watch the recording]({{ item.youtubeUrl }})  {% endif %}
{% if item.abstract and item.abstract != '' %}##### Abstract:
{{ item.abstract }}{% endif %}
{% assign bioCount = item.speakers | where_exp: "item", "item.bio" | where_exp: "item", "item.bio != ''" | size %}
{% if bioCount != 0 %}
##### Bio:
{% for speaker in item.speakers %}  
###### {{ speaker.name }}: 
{{ speaker.bio }}
{% endfor %} 
{% endif %}
{% endfor %}  
