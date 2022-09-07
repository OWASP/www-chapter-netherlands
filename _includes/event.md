### {{ event.date | date: "%B %-d %Y"}}
{{ event.information }}  

{% if item.location and item.location != '' %}Location: {{ event.location }}  {% endif %}
{% if item.address and item.address != '' %}Address: {{ event.address }}  {% endif %}
{% if item.locationUrl and item.locationUrl != '' %}Link: {{ event.locationUrl }}  {% endif %}
{% if item.meetupUrl and item.meetupUrl != '' %}  
Please register via: {{ event.meetupUrl }}  {% endif %}

{% for item in event.items %}{% if item.start and item.start != '' %}{{ item.start }} - {{ item.end }} - **{{ item.title }}**  
{% endif %}{% endfor %}  

{% assign talks = event.items | where: "type", "talk" %}  

{% for item in talks %} 
#### {{ item.title }}
{% if item.presentationUrl and item.presentationUrl != '' %}[Download the presentation]({{ item.presentationUrl }})  {% endif %}
{% if item.youtubeUrl and item.youtubeUrl != '' %}[Watch the recording]({{ item.youtubeUrl }})  {% endif %}
##### Abstract:
{{ item.abstract }}
##### Bio:
{% for speaker in item.speakers %}  
###### {{ speaker.name }}: 
{{ speaker.bio }}
{% endfor %} 
{% endfor %}  
