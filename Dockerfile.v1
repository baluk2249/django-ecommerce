# Stage 1 : Build the applicatin
FROM python:3.9-slim as builder
#Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

#Install dependencies
RUN apt-get update && apt-get install -y build-essential  libpq-dev && rm -rf /var/lib/apt/lists/*

#Create and set working directory
WORKDIR /app/

#Install Python dependencies
COPY requirements.txt /app/
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

#COPY the application code 

COPY . /app/

#RUN application

CMD ["python","manage.py","runserver","0.0.0.0:8000"]