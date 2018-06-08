Synth
-----

[![Docker Stars](https://img.shields.io/docker/stars/tecweb/synth.svg?maxAge=2592000)](https://hub.docker.com/r/tecweb/synth/)
[![Docker Pulls](https://img.shields.io/docker/pulls/tecweb/synth.svg?maxAge=2592000)](https://hub.docker.com/r/tecweb/synth/)

Synth is a development environment for building hypermedia applications that are modeled 
according to SHDM (Semantic Hypermedia Design Method). It provides a set of modules that 
receive, as input, models  generated in each step of SHDM and produces, as output, the 
hypermedia application described by these models. Synth also provides an authoring environment 
that facilitates the adding and editing of these models through a GUI that can run on 
any web browser. 

For more details see this publication: https://link.springer.com/chapter/10.1007/978-3-642-22233-7_9 (full text download available).
Here is a video of a demo of Synth: https://www.researchgate.net/profile/Daniel_Schwabe/publication/325654019_Synth_Demo_video/data/5b1ac2ee45851587f29d268d/Demo-App-ICWE-2011.mov
Synth was built as part of the master thesis dissertation in Informatics of  Mauricio Henrique de Souza Bomfim, at PUC-Rio.

It is in a very early stage; please be advised you may find some bugs when using Synth. 
Please report if you find any bug.

INSTALLING
----------
Install JRuby (http://jruby.org) 1.6.8

Install Bundler
```
$ jgem install bundler
```

Install dependencies
```
$ cd /path/to/synth
$ bundle install
```
RUNNING (Ruby 1.9)
-------
```
$ jruby --1.9 -S script/server
```
Open on your internet browser: [http://localhost:3000](http://localhost:3000)

RUNNING with MIRA
-----------------

Open on your internet browser: [http://localhost:3000/mira.html](http://localhost:3000/mira.html)

Mira Docs: [http://mira.tecweb.inf.puc-rio.br/docs](http://mira.tecweb.inf.puc-rio.br/docs)

MIRA files
----------

* Locations:
``` bash
$ cd /path/to/synth/public/js
```    
* Path to edit your interface:
``` bash
$ edit /path/to/synth/public/js/app.js
```
* RUN your application:
    
Open on your internet browser: [http://localhost:3000/mira.html?app=app](http://localhost:3000/mira.html?app=app)

[REST examples](doc/Rest.md)

INSTALLING WITH DOCKER
----------------------

#### 1) Install Docker

  [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
  
  On Windows and Mac OS, you can use Docker Toolbox:
  
  [https://www.docker.com/products/docker-toolbox](https://www.docker.com/products/docker-toolbox)
  
#### 2) Run container of synth by the first time:
 
  this can take while.

```
$ docker run --name my_synth -p 3000:3000 tecweb/synth
```

  
#### 3) Access synth:

  [http://192.168.99.100:3000](http://192.168.99.100:3000)
  
#### 4) Access Mira:

  [http://192.168.99.100:3000/mira.html](http://192.168.99.100:3000/html)
  
#### 5) Stop synth container:

``` bash
$ docker stop my_synth
```
  
#### 6) Running other times to not lose your data and applications:

``` bash
$ docker start my_synth
```

Export your application
=======================

#### 1) Run container compress command:

  Considering your application is called *my_app*

``` bash
$ docker exec my_synth tar -zcvf public/my_app.tar.gz applications/my_app
```

#### 2) Download compress file from your browser:

  [http://192.168.99.100:3000/my_app.tar.gz](http://192.168.99.100:3000/my_app.tar.gz)

Import your data from external file
===================================

#### 1) Run Synth
    Create and application,e.g., *my_app*. Do not activate it (i.e., leave it as "false" in the apps menu).
    
#### 2) Shutdown and close Synth

#### 3) Put your RDFXML formatted file (e.g., my_app.owl, as exported from Protegé) with the data in the Synth folder/directory.

#### 4) Open a command prompt/shell window, and change the active diretory to Synth's home directory
    Run the following command
    
``` bash
$ 
    jruby --1.9 -S script/import my_app.owl model=my_app format=rdfxml
```
