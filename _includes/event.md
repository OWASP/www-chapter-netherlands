### {{ event.date | date: "%B %-d %Y"}}
{{ event.information }}  

Location: {{ event.location }}  
Address: {{ event.address }}  

{% for item in event.items %}  
{{ item.start }} - {{ item.end }} - **{{ item.title }}**  
{% endfor %}  

{% for item in event.items %}  
#### {{ item.title }}

##### Abstract:
{{ item.abstract }}
##### Bio:
{% for speaker in item.speakers %}  
###### {{ speaker.name }}: 
{{ speaker.bio }}
{% endfor %} 
{% endfor %}  
