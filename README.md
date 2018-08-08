# STEPS OF SETUP Django in virtual ENV With apache2

cd /var/www <br/>
mkdir python_app<br/>
cd python_app <br/>
sudo virtualenv -p python3 env <br/>
source env/bin/activate<br/>

sudo env/bin/python3.6 -m pip install django<br/>

sudo env/bin/django-admin.py startproject myapp .<br/>
## sudo apt-get install libapache2-mod-wsgi-py3
