---
layout: default
permalink: /blogs
---

<ul>
	{% for post in site.categories.blog %}
		<li>
			<a href="{{ post.url}}">{{ post.title }}</a> - {{ post.date }}
		</li>
	{% endfor %}
</ul>