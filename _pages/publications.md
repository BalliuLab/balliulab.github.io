---
layout: archive
title: "Software"
permalink: /publications/
author_profile: true
---

[FastGxC](https://github.com/BrunildaBalliu/FastGxC): a computationally efficient and statistically powerful software for detecting context-specific QTL effects in multi-context genomic studies with shared noise. 

[CONTENT](https://github.com/cozygene/CONTENT): a computationally efficient and powerful method for multi-context transcriptome-wide association studies with shared 

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
