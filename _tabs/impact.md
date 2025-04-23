---
layout: page
icon: fas fa-hand-holding-heart
title: Impact
order: 3
---

# Our Impact

The SPWF Foundation is dedicated to creating meaningful change through our carefully selected projects. This page highlights the collective impact of our funding initiatives over time.

## Impact By Numbers

- **Projects Funded**: 12 initiatives across 8 countries
- **Total Funding**: £1.5 million distributed to worthwhile projects
- **People Reached**: Over 50,000 individuals positively impacted
- **Sustainable Development Goals**: Contributing to 7 of the UN's SDGs

## Annual Reports

Our commitment to transparency means we provide detailed reporting on our foundation's activities and impact.

{% assign current_year = site.time | date: "%Y" | minus: 0 %}
{% for year in (2020..current_year) reversed %}
### {{ year }} Annual Impact

{% if year == 2024 %}
- Provided £350,000 in funding across 4 new projects
- Expanded clean water initiatives to 2 additional regions
- Launched our first educational technology program
- [Download Full {{ year }} Report](#)
{% elsif year == 2023 %}
- Distributed £400,000 to 3 long-term projects
- Completed first 3-year funding cycle with measurable outcomes
- Established formal impact assessment framework
- [Download Full {{ year }} Report](#)
{% elsif year == 2022 %}
- Allocated £300,000 to 3 projects
- Introduced multi-year funding commitments
- Expanded board of advisors to include field experts
- [Download Full {{ year }} Report](#)
{% elsif year == 2021 %}
- Provided £250,000 in project funding
- Formalized project selection criteria
- Established monitoring and evaluation processes
- [Download Full {{ year }} Report](#)
{% elsif year == 2020 %}
- Initial funding of £200,000 to 2 pilot projects
- Foundation formally established
- Core mission and values defined
- [Download Full {{ year }} Report](#)
{% endif %}

{% endfor %}
