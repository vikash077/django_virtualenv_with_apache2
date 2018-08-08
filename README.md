# STEPS OF SETUP Django in virtual ENV With apache2

<b>Create a directory :</b><br/>
<pre>
cd /var/www
mkdir python_app
sudo chown &lt;user&gt;:&lt;userGroup&gt; python_app -R
</pre>

<b>Create virtual environment for python3:</b><br/>
<pre>
cd python_app
virtualenv -p python3 env
</pre>

<b>Activate your virtual environment:</b><br/>
<pre>
source env/bin/activate
</pre>

<b>And if you want to deactivate virtual environment:</b><br/>
<pre>
deactivate
</pre>

<b>Install Django:</b><br/>
<pre>env/bin/python3.6 -m pip install django</pre>

<b>Start new project in Django:</b><br/>
<pre>env/bin/django-admin.py startproject myapp .</pre>

<b>Test And Try Django:</b><br/>
<pre>env/bin/python manage.py runserver 0.0.0.0:8080</pre>

Check it http://localhost:8080/ <br/>


### NOW SET UP IT WITH APACHE2  mod-wsgi
if apache not installed : <b>apt-get install apache2</b><br/>

<b>Install mod_wsgi for apache2 :</b><br/>
sudo apt-get install libapache2-mod-wsgi-py3<br/>


<b>Change apache configurations :</b><br/>
sudo vim /etc/apache2/sites-enabled/000-default.conf<br/>
add below settings in "/etc/apache2/sites-enabled/000-default.conf" <br/>

<pre>
WSGIDaemonProcess python_app python-path=/var/www/python_app:/var/www/python_app/env/lib/python3.6/site-packages
WSGIProcessGroup python_app
WSGIScriptAlias /var/www/python_app/myapp/wsgi.py
</pre>

<b>NOW Restart your server:</b><br/>
service apache2 restart<br/>

<b>Check it now:</b><br/>
http://localhost/<br/>

