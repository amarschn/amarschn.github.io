General Notes
=============

To test on http://localhost:4000/:

	bundle exec jekyll serve


To create a new post:

	sudo python jekyll-post.py [-w] [-d date] [title]

	Example : sudo python jekyll-post.py -d "2015-06-15" -t "misc" "Test Post"

To create a new project:

1. Create a new file in the 'projects' folder: '[project-name].html' or '[project-name].md'.

2. Make sure in the frontmatter there is no 'title', otherwise it will show up in the nav bar.

3. Add template to the '[project-name].html' file (REMEMBER TO CHANGE THE TAGS TYPE) if there are going to be more than 1 post:
	
		<div class="home">
		  <h1 class="page-heading">Projects</h1>

		  <ul class="post-list">
		    {% for post in site.tags["misc"] %}
		            <li>{{ post.title }}</li>
		    {% endfor %}
		  </ul>
		</div>


4. Add project link to 'projects.html'.