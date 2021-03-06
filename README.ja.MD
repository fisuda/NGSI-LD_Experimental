# NGSI-LD Wrapper (NGSI-LD ラッパー)

[![](https://nexus.lab.fiware.org/repository/raw/public/badges/chapters/core.svg)](https://www.fiware.org/developers/catalogue/)
[![MIT license][license-image]][license-url]
[![Docker badge](https://img.shields.io/docker/pulls/fiware/ngsi-ld_wrapper.svg)](https://hub.docker.com/r/fiware/ngsi-ld_wrapper/)
[![NGSI-LD badge](https://img.shields.io/badge/NGSI-LD-red.svg)](http://www.etsi.org/deliver/etsi_gs/CIM/001_099/004/01.01.01_60/gs_CIM004v010101p.pdf)
<br/>
[![Build badge](https://img.shields.io/travis/FIWARE/NGSI-LD_Wrapper.svg?branch=master "Travis build status")](https://travis-ci.org/FIWARE/NGSI-LD_Wrapper/?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/Fiware/NGSI-LD_Wrapper/badge.svg?branch=master)](https://coveralls.io/github/Fiware/NGSI-LD_Wrapper?branch=master)

このプロジェクトの目的は、[FIWARE Context Broker](https://github.com/fiware/context.Orion) 上にある、プロキシによって生成されるラッパーに基づいて [NGSI-LD](https://docbox.etsi.org/ISG/CIM/Open/ISG_CIM_NGSI-LD_API_Draft_for_public_review.pdf) の実装を作成することです。[FIWARE NGSI](http://fiware.github.io/specifications/ngsiv2/latest/) を活用する NGSI-LD は、[ETSI ISG CIM](https://portal.etsi.org/tb.aspx?tbid=854&SubTB=854) によって開発された国際標準であり、複数のシナリオでのコンテキスト情報の提供、使用、およびサブスクライブを目的としています。これにより、IoT だけでなく、さまざまな情報源からの情報へのリアルタイムのアクセスが可能になります。

FIWARE NGSI の根幹となる、[OMA NGSI-9/10 情報モデル](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/NGSI-9/NGSI-10_information_model) は、[JSON-LD](https://json-ld.org/primer/latest/) の機能を活用した、リンクト・データ (エンティティのリレーションシップ)、[プロパティ・グラフ](https://neo4j.com/lp/book-graph-databases/)、セマンティクスをよりよくサポートするために ETSI CIM によって強化されています。結果の仕様は、**NGSI-LD** と命名されました。注目すべきは、[NGSI-LD 情報モデル](doc.ja/NGSI-LD_Information_Model.md) が OMA NGSI-9/10 情報モデル の一般化であることです。結果として、両方の情報モデルの間に良好なレベルの互換性と明確な移行パスが期待されます。

このラッパーは、[FIWARE Context Broker](https://github.com/fiware/context.Orion) 上で動作し、基本的に、NGSIv2 (JSON) 表現と **NGSI-LD** (JSON-LD) 表現の間で適応します。

NGSI-LD の使用例を[ここ](doc.ja/example.md)に示します。

## ビルド方法

### 前提条件

* Java 8
* Scala runtime
* SBT build tool

```console
$ sbt compile
$ export NGSI_Endpoint=http://<Your_NGSI_Endpoint i.e. Orion's host:port>
$ sbt jetty:start
```

## テスト方法

```console
$ sbt test
```

## Docker を使った実行方法

```console
$ docker run -e NGSI_Endpoint="http://<Your_NGSI_Endpoint i.e. Orion's host:port>" fiware/ngsi-ld_wrapper

$ curl http://localhost:1030/version
```

## Docker Compose を使った実行方法

```console
$ wget https://raw.githubusercontent.com/Fiware/NGSI-LD_Wrapper/master/docker-compose.yml
$ docker-compose up

$ curl http://localhost:1030/version
```

## 設定を確認する方法 (NGSI endpoint)

```console
$ curl http://localhost:1030/configuration
```

## API オペレーションを呼び出す方法

```console
$ curl http://localhost:1030/api/entities/
```

## 参照 :

https://github.com/fiware/dataModels

https://github.com/fiware/context.Orion

[license-image]: https://img.shields.io/github/license/fiware/tutorials.Administrating-XACML.svg
[license-url]: LICENSE
