# STEPS OF SETUP Django in virtual ENV With apache2

<b>create a directory :</b><br/>

cd /var/www <br/>
mkdir python_app<br/>
sudo chown &lt;user&gt;:&lt;userGroup&gt; python_app -R <br/>

<b>Create virtual Environment with python3:</b><br/>
cd python_app <br/>
virtualenv -p python3 env <br/>

<b>Activate Your Virtual Environment:</b><br/>
source env/bin/activate<br/>

<b>And You want to deactivate virtual environment:</b><br/>
deactivate<br/>

<b>Install Django:</b><br/>
env/bin/python3.6 -m pip install django<br/>

<b>Start new project in Django:</b><br/>
env/bin/django-admin.py startproject myapp .<br/>

<b>Test And Try Django:</b><br/>
env/bin/python manage.py runserver 0.0.0.0:8080<br/>

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

