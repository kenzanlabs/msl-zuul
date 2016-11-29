MSL-ZUUL
========

The MSL Zuul Router handles routing of all external calls to their corresponding endpoints based on security location, and other variables.s

* Zuul tehcnology is part of the Netflix OSS stack. Documentation is found [here](https://github.com/Netflix/zuul/wiki)

* Versioning is explained [here](http://projects.dev-charter.net/confluence/display/ZUUL/Zuul+versioning)

* Zuul works by the use of filters that can alter requests. Filters can re-route requests, change headers and return a not-authorized response based on credentials passed in the request. The filters themselves are written in [Groovy](http://beta.groovy-lang.org/docs/latest/html/documentation/) The types of filters are explained in the [wiki documentation](https://github.com/Netflix/zuul/wiki/How-it-Works)
 
Configuration
=============

By default msl-zuul starts on port 9000 specified in the jetty configuration in the `pom.xml` file. 
One can override this configuration by passing in the `port` argument 

```
mvn jetty:run -Dport=8089
```

Zuul will then load the `zuul.properties` file and map the `niws.clientlist` properties for each of the eureka services that are up.

One can then simply access any of the edge services by going through the zuul URL. For example, if running locally and on port 9000 

`https://localhost:9000/catalog-edge/browse/albums`

PACKAGING
=========

The default packaging for the project is a web application type `.war` file. 

>***NOTE*** Before generating it, one must change the zuul.properties zuul.filter.x.path's to reflect compiled sources.