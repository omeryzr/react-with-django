<img src="https://cdn-images-1.medium.com/max/1000/1*1Kb4nfsuXuuYeRmqIo3oyg.png">
<article class="markdown-body entry-content" itemprop="text"><h1><a href="#django" aria-hidden="true" class="anchor" id="user-content-scrapy"></a>README - How to Use React with Django 2018</h1>
<p>This project was created to learn <b>React with Django</b></p>


<h2><a href="#table-of-contents" aria-hidden="true" class="anchor" id="user-content-table-of-contents"></a>Table of Contents</h2>

<ul>
<li><a href="#django">Create Django Project</a></li>
<li><a href="#react">Create React App</a></li>
<li><a href="#configure">Configure Django Settings.py, Urls.py and Manage.py</a></li>
</ul>

<h2><a href="#django" aria-hidden="true" class="anchor" id="user-content-what"></a>Step 1 : Create Django Projec</h2>
<q>Firstly, we create a python environment for our django project. and creating django start project in this environment.</q>


<h2></h2>
<h2><a href="#commands" aria-hidden="true" class="anchor" id="user-content-commands"></a>Create Django Project</h2>
  <pre>
  $ python3 -m venv ReactwithDjango && cd ReactwithDjango
  $ source bin/activate
  $ pip install django
  $ django-admin.py startproject reactwithdjango && cd reactwithdjango
  $ ./manage.py runserver
  </pre>
  
  

<h2><a href="#react" aria-hidden="true" class="anchor" id="user-content-howtoinstall"></a>Step 2 : Create React App</h2>
<p>Django project is completed. now creating react, but nodejs and npm not installed, now install nodejs and install npm.</p>

<pre>$ sudo apt-get install nodejs npm</pre>

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts.

<pre>
$ npx create-react-app frontend && cd frontend
$ npm start
</pre>

<pre> 
$ npm run build
</pre>

<pre>
That’s project’s all filesreactwithdjango/
└─ frontend
  └─ build
  └─ node_modules
  └─ public
   └─ favicon.ico
   └─ index.html
   └─ manifest.json
   └─ src
└─ reactwithdjango
  └─ __init__.py
  └─ settings.py
  └─ urls.py
  └─ wsgi.py
db.sqlite3
manage.py
package-lock.json
</pre>

<h2><a href="#configure" aria-hidden="true" class="anchor" id="user-content-quickstart"></a>Step 3 : Configure Django Settings.py, Urls.py and Manage.py</h2>

<p>You need to update the directory addresses for the theme on settings.py</p>

settings.py
<pre>
TEMPLATES = [
    {        
        'DIRS': [
            os.path.join(BASE_DIR, 'frontend', 'build'),
        ],
</pre>
Again, you need to write under settings.py the following code for your static documentation

<pre>
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'frontend', 'build', 'static')
]
</pre>

urls.py
<pre>
from django.urls import re_path
from django.views.generic import TemplateView
urlpatterns = [
    re_path('.*', TemplateView.as_view(template_name='index.html')),
...
</pre>

manage.py
<pre>
try:
    if sys.argv[2] == 'react':
        project_root = os.getcwd()
        os.chdir(os.path.join(project_root, "frontend"))
        os.system("npm run build")
        os.chdir(project_root)
        sys.argv.pop(2)
except IndexError:
    execute_from_command_line(sys.argv)
else:
    execute_from_command_line(sys.argv)
</pre>

After finishing editing, Runnn!

<pre>
./manage.py runserver react
</pre>

<pre>Completed. Now work on index.html in the public file. Happy hacking!</pre>

You can examine in my story : <link href="https://medium.com/@omeryazir/how-to-use-react-with-django-2018-8dd0d4b22392">https://medium.com/@omeryazir/how-to-use-react-with-django-2018-8dd0d4b22392</link>
</article>
