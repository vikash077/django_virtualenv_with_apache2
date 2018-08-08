# STEPS OF SETUP Django in virtual ENV With apache2

cd /var/www <br/>
mkdir python_app<br/>
sudo chown <user>:<userGroup> python_app -R
cd python_app <br/>
virtualenv -p python3 env <br/>
source env/bin/activate<br/>

env/bin/python3.6 -m pip install django<br/>

env/bin/django-admin.py startproject myapp .<br/>

env/bin/python manage.py runserver 0.0.0.0:8080<br/>

Check it http://localhost:8080/ <br/>


## NOW SET UP IT WITH APACHE2  mod-wsgi

sudo apt-get install libapache2-mod-wsgi-py3
