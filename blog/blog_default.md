---
layout: default
permalink: /blog
---

<ul>
	{% for post in site.categories.blog %}
		<li>
			<a href="{{ post.url}}">{{ post.title }}</a> - {{ post.date }}
		</li>
	{% endfor %}
</ul>