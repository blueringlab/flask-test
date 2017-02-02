FROM python:2.7

# Install Python PIP
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential

# Copy codes
COPY ./wsgi-scripts /var/www/wsgi-scripts

# Install Python requirements
WORKDIR /var/www/wsgi-scripts
RUN pip install -r requirements.txt


# Install Apache2 and mod_wsgi library
RUN apt-get update
RUN apt-get install -y openssh-server apache2 libapache2-mod-wsgi supervisor
RUN mkdir -p /var/lock/apache2 /var/run/apache2 /var/run/sshd /var/log/supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf


# Install VirtualHost conf for Apache server
COPY soup.conf /etc/apache2/sites-available/soup.conf
COPY soup.conf /etc/apache2/sites-enabled/soup.conf

EXPOSE 5000

#CMD ["/usr/bin/supervisord"]
