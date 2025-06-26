* `models.py` file contain the way that we interact with data base
	* If you make any change on this file you need to update your database
	  `python manage.py makemigrations blog`
	  `python manage.py migrate`
# Django Shell
`python manage.py shell`: open a Django shell that knows about your project structure, a way to interact with models
* You can even query your database in this :D
  `Post.objects.all()`
  `Post.objects.filer("First Post")`