---
layout: home
permalink: /
title: "Sang Yeon Yoon"
excerpt: "I study the internal representations and information-processing mechanisms of Multimodal Large Language Models, and use those insights to improve inference efficiency and mitigate hallucinations."
redirect_from:
  - /about/
  - /about.html
---

<!-- ---------------------------------------------------------------------
  Single vertical-scroll page. No subpages.
  Section ids below must match the anchors in _data/navigation.yml.

  Papers are NOT written here - they live in _data/publications.yml and are
  rendered by the two includes at the bottom of this file.
---------------------------------------------------------------------- -->

{%- assign a = site.data.author -%}
<section id="about">
<div class="container about-grid">

<div class="about-text prose" markdown="1">

<h1 class="name">{{ a.name }}</h1>
<p class="title-line">{{ a.role }}, {{ a.affiliation }}</p>

I am an undergraduate student in Computer Engineering at Pukyong National
University and currently a research intern in the Computer Vision and
Signal Processing Lab (CVSP Lab) at Pusan National University.

My research focuses on understanding the internal representations and
information-processing mechanisms of Multimodal Large Language Models,
and leveraging these insights to improve inference efficiency and mitigate
hallucinations.

More recently, I have been interested in extending this perspective to
Multi-Agent Systems.

<p class="about-links">
  {% if a.email %}<a href="mailto:{{ a.email }}">{% include icon.html name="email" %}<span>Email</span></a>{% endif %}
  {% if a.github %}<a href="https://github.com/{{ a.github }}">{% include icon.html name="github" %}<span>GitHub</span></a>{% endif %}
  {% if a.linkedin %}<a href="https://www.linkedin.com/in/{{ a.linkedin }}">{% include icon.html name="linkedin" %}<span>LinkedIn</span></a>{% endif %}
  {%- comment -%}
    Scholar, ORCID and CV are deliberately left out. _includes/icon.html still
    carries their icons, so re-adding one is a single line:
    {% if a.scholar %}<a href="{{ a.scholar }}">{% include icon.html name="scholar" %}<span>Google Scholar</span></a>{% endif %}
    {% if a.orcid %}<a href="{{ a.orcid }}">{% include icon.html name="orcid" %}<span>ORCID</span></a>{% endif %}
    {% if a.cv %}<a href="{{ a.cv | relative_url }}">{% include icon.html name="cv" %}<span>CV</span></a>{% endif %}
  {%- endcomment -%}
</p>

</div>

<div class="about-photo">
  {% if a.photo %}
  <div class="photo-circle"><img class="profile-img" src="{{ a.photo | relative_url }}" alt="{{ a.name }}"></div>
  {% else %}
  <div class="photo-circle photo-circle--empty" aria-hidden="true">PHOTO</div>
  {% endif %}
</div>

</div>
</section>

<section id="interests">
<div class="container">
  <h2 class="section__hd">Research Interests</h2>
  <ul class="interests">
    <li><b>Model efficiency</b></li>
    <li><b>Mechanistic analysis for model improvement</b></li>
    <li><b>Multi-Agent Systems</b></li>
  </ul>
</div>
</section>


<section id="experiences">
<div class="container">
  <h2 class="section__hd">Experiences</h2>

  <h3 class="subhd">Research</h3>
  <ul class="entries">
    <li>
      <div class="entry__when">Jan 2026 &ndash; Present</div>
      <p class="entry__what">
        <b>Research Intern</b>
        <span class="entry__where"><a href="https://www.pnu-cvsp.com/">CVSP Lab</a>, Pusan National University</span>
        <span class="entry__note">Advisor: Prof. Kyeongbo Kong</span>
      </p>
    </li>
  </ul>

  <h3 class="subhd">Projects</h3>
  <ul class="entries">
    <li class="entry--logo">
      <div class="entry__when">May 2026 &ndash; Nov 2026</div>
      <p class="entry__what">
        <b>Object-change-based spatial tidiness detection for home robots</b>
        <span class="entry__where">In collaboration with LG Electronics</span>
        <span class="entry__note">Co-Researcher</span>
      </p>
      {%- comment -%}
        Partner logo, right-hand slot of the row. Drop the file in
        images/logos/ as lg-electronics.<ext> and it appears; until then the
        slot stays empty, so a missing file never shows a broken image.
        The first extension that exists wins, webp first as it is the smallest.
      {%- endcomment -%}
      {%- assign logo_exts = "webp,svg,png,jpg,jpeg" | split: "," -%}
      {%- assign logo = false -%}
      {%- for ext in logo_exts -%}
        {%- unless logo -%}
          {%- assign candidate = "/images/logos/lg-electronics." | append: ext -%}
          {%- assign logo = site.static_files | where: "path", candidate | first -%}
        {%- endunless -%}
      {%- endfor -%}
      <div class="entry__logo">
        {%- if logo %}<img src="{{ logo.path | relative_url }}" alt="LG Electronics" loading="lazy">{% endif -%}
      </div>
    </li>
  </ul>
</div>
</section>

{% include pub-section.html section="conference" id="publications" title="Selected Publications" %}
