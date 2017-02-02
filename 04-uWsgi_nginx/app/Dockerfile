FROM python:2.7

# Install Python PIP
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential

# Copy codes
COPY ./soup /opt/soup

# Install Python requirements
WORKDIR /opt/soup
RUN pip install -r requirements.txt
RUN mkdir /var/run/soup

EXPOSE 5000

ENTRYPOINT uwsgi --socket 0.0.0.0:5000 --protocol=http -w myapp