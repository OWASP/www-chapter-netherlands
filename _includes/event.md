### {{ event.date | date: "%B %-d %Y"}}
{{ event.information }}  

Location: {{ event.location }}  
Address: {{ event.address }}  

{% for item in event.items %}{{ item.start }} - {{ item.end }} - **{{ item.title }}**  
{% endfor %}  

{% assign talks = event.items | where: "type", "talk" %}  

{% for item in talks %} 
#### {{ item.title }}
{% unless item.presentationUrl == "" or item.presentationUrl == nil %}[Download the presentation]({{ item.presentationUrl }})  {% endif %}
{% unless item.youtubeUrl == "" or item.youtubeUrl == nill %}[Watch the recording]({{ item.youtubeUrl }})  {% endif %}
##### Abstract:
{{ item.abstract }}
##### Bio:
{% for speaker in item.speakers %}  
###### {{ speaker.name }}: 
{{ speaker.bio }}
{% endfor %} 
{% endfor %}  
