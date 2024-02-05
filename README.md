#Credit to "https://www.datasciencebytes.com/bytes/2015/02/24/running-a-flask-app-on-aws-ec2/" however this guide is very outdated, and had issues even with new workarounds.
1.
sudo apt-get update
sudo apt-get install apache2
sudo apt-get install python3-pip
*Update outdated libraries*
sudo apt-get install libapache2-mod-wsgi-py3
*Restart Services*

2.
pip3 install virtualenv
python3 -m virtualenv venv
source venv/bin/activate
sudo pip install flask
sudo apachectl restart

3.
mkdir ~/myflaskapp
sudo ln -sT ~/myflaskapp /var/www/html/flaskapp
cd ~/myflaskapp
echo "Hello World" > index.html

TESTING
"Error" when testing (your instance public DNS)/flaskapp
--------------------------------------------------------------------------------------------
Forbidden
You don't have permission to access this resource.

Apache/2.4.52 (Ubuntu) Server at ec2-18-222-225-115.us-east-2.compute.amazonaws.com Port 80
--------------------------------------------------------------------------------------------

4.
sudo nano flaskapp.py (create file)
sudo nano flaskapp.wsgi (create file)
sudo nano /etc/apache2/sites-enabled/000-default.conf (modify file)
sudo apachectl restart

TESTING
Same "Error" when testing (your instance public DNS)
--------------------------------------------------------------------------------------------
Forbidden
You don't have permission to access this resource.

Apache/2.4.52 (Ubuntu) Server at ec2-18-222-225-115.us-east-2.compute.amazonaws.com Port 80
--------------------------------------------------------------------------------------------

Note: I stopped here as I was unable to test any python code. I attempted to modify a few root config file permissions by adding "Require all granted" to fix the issue. I also tried every solution I could find on stack overflow, nothing worked.
