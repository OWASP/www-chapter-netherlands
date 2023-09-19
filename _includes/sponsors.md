## Sponsors
{%- assign currentYear = site.time | date: "%Y" %}

{% if currentYear == "2023" -%}
  {% include sponsors-benelux-2022.md %} 
{%- endif %}

{% if currentYear == "2023" or currentYear == "2024" -%}
  {% include sponsors-benelux-2023.md %} 
{%- endif %}
