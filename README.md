# imdb_data_import_elastic
Prepares the IMDB dataset of various interface like actor , actresses for bulk import of Elasticsearch 

This is a simple python script which reads the file (Actor / actresses) from imdb , prepare the json out of that after exracting and write the same to a file.

Output of this script will be written as .json file , which can be further used to bulk import to elasticsearch as below.

Data Source
-----------
http://www.imdb.com/interfaces

> Plain Text Data Files > actresses.list.gz > actresses.list > actresses.json

    ex. : Download the actresses data as : wget ftp://ftp.funet.fi/pub/mirrors/ftp.imdb.com/pub/actresses.list.gz
    unzip as : gunzip actresses.list.gz

Run Python script to create json file for import
--------------------

    python imdb_actor_import.py 


Import the json data via curl
--------------------

    curl -s -XPOST localhost:9200/actresses/_bulk --data-binary @actresses.json;
