# STEPS OF SETUP Django in virtual ENV With apache2

cd /var/www <br/>
mkdir python_app<br/>
sudo chown &lt;user&gt;:&lt;userGroup&gt; python_app -R <br/>
cd python_app <br/>
virtualenv -p python3 env <br/>
source env/bin/activate<br/>

env/bin/python3.6 -m pip install django<br/>

env/bin/django-admin.py startproject myapp .<br/>

env/bin/python manage.py runserver 0.0.0.0:8080<br/>

Check it http://localhost:8080/ <br/>


### NOW SET UP IT WITH APACHE2  mod-wsgi
if apache not installed : apt-get install apache2<br/>

sudo apt-get install libapache2-mod-wsgi-py3<br/>
sudo vim /etc/apache2/sites-enabled/000-default.conf<br/>

<pre>
WSGIDaemonProcess python_app python-path=/var/www/python_app:/var/www/python_app/env/lib/python3.6/site-packages
WSGIProcessGroup python_app
WSGIScriptAlias /var/www/python_app/myapp/wsgi.py
</pre>

NOW Restart your server:<br/>
service apache2 restart<br/>

Check it now:<br/>
http://localhost/<br/>

