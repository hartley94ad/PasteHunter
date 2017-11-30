# PasteHunter
PasteHunter is a python3 application that is designed to query a collection of sites that host publicliy pasted data. 
For all the pasts it finds it scans the raw contents against a series of yara rules looking for information that can be used 
by an org or a researcher.

## Supported Sites
Pastehunter currently has support for the following sites:
 - pastebin.com
 - dumpz.org
 - gist.github.com

Support for the following sites is listed as ToDo:
 - paste.ee


# Installation

## PreReqs

### Pastebin

You need a Pro account on pastebin that has access to the scraping API.
https://pastebin.com/api_scraping_faq

### GitHub
Github needs an oauth token to stop it hitting the free ratelimit. 
Create one at https://github.com/settings/tokens

YOU DO NOT NEED TO GIVE IT ANY ACCESS PERMISSIONS

# Installation

## Local install 

### Elastic Search
https://www.elastic.co/guide/en/elasticsearch/reference/current/deb.html

### Kibana
https://www.elastic.co/guide/en/kibana/current/deb.html

### Yara
https://yara.readthedocs.io/en/v3.6.0/gettingstarted.html#compiling-and-installing-yara

If you have yara errors check the installed version numbers for yara and yara-python match the lastest versions.

### PasteHunter
git clone https://github.com/kevthehermit/pastehunter

### Python / Deps
Python 3
```pip3 install -r requirements.txt```

## Using Docker

Install Docker & docker-compose

`docker build . -t pastehunter`

## Using Docker-compose

### Running all the applications
Run `docker-compose up -d`

#### Kibana

Kibana is running only on the localhost interface on default port (5601).

Kibana use the default login and password : `elastic` and `changme`

Kibana is using the static IP address : 172.16.10.12 in the `esnet`  network

#### Elasticsearch

Elasticsearch is running only on the localhost interface on default port 9200.
The mount point is `/usr/share/elasticsearch/data` by default

#### Pastehunter

You can re-run the pastehunter script by doing `docker-compose up -d`
Docker-compose will use already running instances of Elasticsearch and Kibana


# Configure

copy settings.conf.sample to settings.conf
populate the details.
For the scraping API you need to whitelist your IP on pastebin. No API key is required. See the link above



# Running

Start the application with ```python3 pastehunter.py```

It may be useful to run in a screen to keep it running in the background. 

## Service 
Service config is coming 
