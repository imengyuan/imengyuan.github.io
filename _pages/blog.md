---
layout: archive
title: "Blogs"
permalink: /blog/
author_profile: true
redirect_from:
  - /blog
---

Blogs

[Github Repo for my bioinfo analysis scripts](https://github.com/imengyuan/Bioinfo-pipelines)

including

* bioinfo_raining: Notes& summary of computational biology training course (for third-year undergrates)
* cpg_analysis: Pipeline notes on chloroplast genome analysis (with a focus on assembly for now )
* RNA_seq: RNA-sequencing based analysis notes (still in preparation)

I also write some blogs, see below

{% include base_path %}

{% for post in site.blog reversed %}
  {% include archive-single.html %}
{% endfor %}