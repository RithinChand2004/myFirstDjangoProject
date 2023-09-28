# myFirstDjangoProject
 
<h2> This is my notes on this project. This project is made with taking references from W3schools.com and Django documentation. </h2>

Django - M(model) - Data that to be represented
         V(view) - Request handler that returns template
	 T(template) - A file containing layout

Django work flow 
Browser requests URL --> Django recieves URL --> Checks url.py --> Finds the view and check view.py --> finds model and imports from model.py --> Displays the data from model in browser from a template

'django-admin startproject <project_name>' - command creates project with required folders and files
'py manage.py runserver' - Run server command
'py manage.py startapp <app_name>' - command creates app with required folders and files

-----------------first project to print hello world -------------------------------------------------------

Go views.py and create a function <funtion_name> and return HttpResponce("Hello World")

create a file urls.py in the same as view.py and route the function created in views.py

now navigate to the urls.py available in the root directory and now route the function created 

-----------------Second project to use HTML templates -----------------------------------------------------

create a folder 'templates' in the <app_name> folder and create a html file <HTMLfile_name>.html.

Write html code in the file

In views.py load the html file from templates and return HttpResponce(template.render())

navigate to settings.py in root folder and go to INSTALLED_APPS list and add <app_name> to the end of the list

'py manage.py migrate' - run command to migrate the unmigratted things

-----------------Create a Model and Insert, Update, Delete data and also update model-----------------------

Navigate to models.py and create a class <class> with few fields <field1>, <field2>

'py manage.py makemigrations members' - Command creates a table in the database

'py manage.py migrate' - Completes table creation in SQL

'py manage.py shell' - Gives an interactive shell to perform operations

'from <app_name>.models import <class>' - write in shell to perform operation on data

'<class>.objecta.all()' - gives the available data

store new values in any variable and save the data. <variable>.save() thus ur first record of data is created.

To update the data store the field again in any variable and overwrite and again save <variable>.save().

To delete store the field in any variable and use <variable>.delete()

Till now we are operating on data but update the model we need to perform some series of operations. First navigate to the models.py file and add or delete the fields
if any field is added then keep null=true so that empty filds can be added to the table 
migrate the fields to table
now go to shell and update the data in those new fields

-----------------Display Data ---------------------------------------------------------------------------------

Create a template to display the models data and update in views to return the context of the data.

create another html in templates to show the details of each entry of the data so that once click on the data entry it will be redirected to the details of the entry

In views.py create a new function to display the details of the data and add it to the urls.py

As we can observe all the files have same template so we can create a master template and with a common template add code in title and body

initialize the code blocks in the other templates and call the data fron the models.

make a main index page like a landing page and update in views and urls.py

For 404 page not found template make 404.html in templates, if any page is not found django automatically opens this template. In settings.py set the debug to false and set allowed hosts.

-----------------Admin -------------------------------------------------------------------------------------------

open the link - http://127.0.0.1:8000/admin/ - to open the admin view

'py manage.py createsuperuser' - to create an user admin

add <model_name> in admin.py	

now we can vies the members but not their names and details - customize it in models.py

In admin page we have options to Create, read, update and delete the data from models

-----------------Static Files --------------------------------------------------------------------------------------

Create a Static folder in members and add a <name>.css file 

write some css script for the project

give the link to css script in master template so that it gets reflected in all the files

To obsere static css in pages .... make the debug to false in settings.py

If it is true django cant load static files. For django to load static file when degub if false pip install whitenoises

'whitenoise.middleware.WhiteNoiseMiddleware', - add the line in malware in settings .py

STATIC_ROOT = BASE_DIR / 'productionfiles'   STATIC_URL = 'static/' Add as two lines in settings.py

'py manage.py collectstatic' - to collect all the static pages

now make the debug to false and allowed hosts in settings.py