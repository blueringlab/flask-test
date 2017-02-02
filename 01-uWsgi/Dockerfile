FROM python:2.7

# Install Python PIP
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential

# Copy codes
COPY ./wsgi-scripts /opt/wsgi-scripts

# Install Python requirements
WORKDIR /opt/wsgi-scripts
RUN pip install -r requirements.txt

EXPOSE 5000

ENTRYPOINT uwsgi --ini myapp.ini 
