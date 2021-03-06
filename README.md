# NGSI-LD Experimental

[![](https://nexus.lab.fiware.org/repository/raw/public/badges/chapters/core.svg)](https://www.fiware.org/developers/catalogue/)
[![MIT license][license-image]][license-url]
[![Docker badge](https://img.shields.io/docker/pulls/fiware/ngsi-ld_wrapper.svg)](https://hub.docker.com/r/fiware/ngsi-ld_wrapper/)
[![NGSI-LD badge](https://img.shields.io/badge/NGSI-LD-red.svg)](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.01.01_60/gs_CIM009v010101p.pdf)
<br/>
[![Build badge](https://img.shields.io/travis/FIWARE/NGSI-LD_Experimental.svg?branch=master "Travis build status")](https://travis-ci.org/FIWARE/NGSI-LD_Experimental/?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/Fiware/NGSI-LD_Experimental/badge.svg?branch=master)](https://coveralls.io/github/Fiware/NGSI-LD_Experimental?branch=master)


The purpose of this project is to study different implementation options of [NGSI-LD](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.01.01_60/gs_CIM009v010101p.pdf). 

The first one is based on a wrapper (incarnated by a proxy) on top of the [FIWARE Context Broker](https://github.com/fiware/context.Orion). Leveraging on [FIWARE NGSI](http://fiware.github.io/specifications/ngsiv2/latest/), NGSI-LD is a Group Specification developed by [ETSI ISG CIM](https://portal.etsi.org/tb.aspx?tbid=854&SubTB=854), intended to define an API to provide, consume and subscribe to context information in multiple scenarios and involving multiple stakeholders. It enables close to real-time access to information coming from many different sources (not only IoT).

The [OMA NGSI-9/10 information model](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/NGSI-9/NGSI-10_information_model), the root basis of FIWARE NGSI, is currently being evolved by ETSI CIM to better support linked data (entity's relationships), [property graphs](https://neo4j.com/lp/book-graph-databases/) and semantics (exploiting the capabilities offered by [JSON-LD](https://json-ld.org/primer/latest/)).  The resulting specification has been named **NGSI-LD**. It is noteworthy that the [NGSI-LD information model](doc/NGSI-LD_Information_Model.md) is a generalization of the OMA NGSI-9/10 information model. As a result, it is expected a good level of compatibility and a clear migration path between both information models.  

The wrapper implementation works on top of the [FIWARE Context Broker](https://github.com/fiware/context.Orion) and basically adapts between NGSIv2 (JSON) representations and the **NGSI-LD** (JSON-LD) representations.

An example illustrating the usage of NGSI-LD can be found [here](doc/example.md).

If you are looking for an Orion-based native implementation of NGSI-LD please have a look at [Orion-LD](https://github.com/fiware/context.Orion-LD).

## How to build

### Prerequisites

* Java 8
* Scala runtime
* SBT build tool

```console
$ sbt compile
$ export NGSI_Endpoint=http://<Your_NGSI_Endpoint i.e. Orion's host:port>
$ sbt jetty:start
```

## How to test

```console
$ sbt test
```

## How to run using Docker

```console
$ docker run -e NGSI_Endpoint="http://<Your_NGSI_Endpoint i.e. Orion's host:port>" fiware/ngsi-ld_wrapper

$ curl http://localhost:1030/version
```

## How to run using Docker Compose

```console
$ wget https://raw.githubusercontent.com/Fiware/NGSI-LD_Wrapper/master/docker-compose.yml
$ docker-compose up

$ curl http://localhost:1030/version
```

## How to check configuration (NGSI endpoint)

```console
$ curl http://localhost:1030/configuration
```

## How to invoke API operations

```console
$ curl http://localhost:1030/ngsi-ld/v1/entities/
```

## See also:

https://github.com/fiware/dataModels

https://github.com/fiware/context.Orion

https://github.com/fiware/NGSI-LD_Tests

[license-image]: https://opensource.org/licenses/MIT
[license-url]: LICENSE

