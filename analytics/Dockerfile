FROM python:3.12.4-slim

WORKDIR /src

# Install a couple of packages to successfully install postgresql server locally
RUN apt update -y && apt install -y build-essential libpq-dev 
#postgresql postgresql-contrib

# Update python modules to successfully build the required modules
COPY . .
RUN pip install --upgrade pip setuptools wheel && pip install -r requirements.txt

ENV POSTGRES_PASSWORD=mypassword
ENV DB_USERNAME=myuser
ENV DB_PASSWORD=${POSTGRES_PASSWORD}
ENV DB_HOST=127.0.0.1
#ENV DB_HOST=host.docker.internal
ENV DB_PORT=5433
ENV DB_NAME=mydatabase

#RUN PGPASSWORD="$DB_PASSWORD" psql --host 127.0.0.1 -U myuser -d mydatabase -p 5433 < <FILE_NAME.sql>

CMD python app.py