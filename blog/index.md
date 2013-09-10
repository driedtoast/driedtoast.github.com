---
layout: default
title: Various crumbs of technology
---

  <h2 class="section-header">{{ page.title }}</h2>
  {% if site.posts %}
  <ul class="posts">
    {% for post in site.posts %}
      <li>
        <div class="date-wrapper">
        <div class="date">
      		<p class="day">
		  	  {{ post.date | date: "%B %d" }}
			    </p>
			    <p class="year">
			    {{ post.date | date: "%Y" }}
			    </p>
         </div> 
         </div>
         <div class="post-blurb"> <a href="{{ post.url }}">{{ post.title }}</a> 
            <p class="post-description">
              {{ post.content | strip_html | condense_spaces | truncate:100 }}...
            </p> 
         </div>
     </li>
    {% endfor %}
  </ul>
  {% endif %} 