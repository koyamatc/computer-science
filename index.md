---
title: Computer-science
layout: default
---

#Computer-science

- - -

__Khan Academy__ で勉強したことなどをまとめています。

===

###index

<div class="row">
	<div class="col-sm-4">
		<h3><span class="label label-info">Cryptography(暗号法)</span></h3>
		<ol class="post-list">
 			{% for post in site.categories.crypto %}
   				<li><a href="{{ post.url }}">{{ post.postTitle }}</a></li>
 			{% endfor %}
		</ol>			
	</div>
	<div class="col-sm-4">
		<h3><span class="label label-info">Information Theory</span></h3>
		<ol class="post-list">
 			{% for post in site.categories.information %}
   				<li><a href="{{ post.url }}">{{ post.postTitle }}</a></li>
 			{% endfor %}
		</ol>			
	</div>
	<div class="col-sm-4">
		<h3><span class="label label-info"></span></h3>
		<ol class="post-list">
 			{% for post in site.categories.xx %}
   				<li><a href="{{ post.url }}">{{ post.postTitle }}</a></li>
 			{% endfor %}
		</ol>			
	</div>


</div>