# daas_docs

## Description

Single repository  to aggregate all documentation of projects related to DaaS (Data as a Service).  This overall projects is to demonstrate a small platform to centralize data, and have it avaialble through an api layer.  It will consist of several source databases, and a SOLR instance for caching.

__daas_py_api__   
is setup as a custom more granular project with a managed DBMS layer.  Is 100% common and re-usable for any domain with configurations.

__daas_py_api_facility__   
is setup as a full Django application including ORM.  

_The idea is to have multple "choices" and models that could be used as boilerplate._

## Table of Contents

- [Technology Stack](#technology-stack)
- [High level project structure](#high-level-project-structure)
- [Project Links](#project-links)
- [Architecture](#architecture)
- [Contact](#contact)

## Technology Stack
__Database__:  
PostgreSQL  
_Liquibase for src migrations_  

__Cache:__  
SOLR

__API Layer:__  
Python (Django)

This layer will handle read/writes of objects.  When records are updated in the database, they will trigger a NOTIFY event; which is being listened by the index layer.

__Index Layer:__ 
Python

This layer will listen to PostgreSQL NOTIFY events, and pull them off.  They will then be processed in batches of either quantity X or time Y.  This way we can control batching.  For example, process every 100 records or every 10 seconds.  Whichever comes first.

[example](https://github.com/nealrout/daas_py_idx/blob/develop/main.py)


__Common components:__  
Logging: Python standarrd logger  
Configuration:  dynaconf  
Secrets: dynaconf/cryptography

## High level project structure

    daas_py                      (ROOT)
    ├───daas_py_auth             (AUTH API)
    ├───daas_py_api              (GENERIC API)
    │   ├───api         
    │   │   ├───domain         
    │   │   ├───api      
    ├───daas_py_idx              (GENERIC INDEXER)
    ├───daas_py_api_facility     (FACILITY API)
    │   ├───facility_api         
    │   │   ├───facility         
    │   │   ├───facility_api      
    ├───daas_py_common           (COMMON)
    │   ├───util                 
    ├───daas_py_config           (CONFIG)

## Project Links
### [daas_db](https://github.com/nealrout/daas_db) - PostgreSQL Liquibase

### [daas_py_auth](https://github.com/nealrout/daas_py_auth) - Django Authorize/Authenticate API

### [daas_py_api](https://github.com/nealrout/daas_py_api) - Django Generic API (Main)

### [daas_py_api_facility](https://github.com/nealrout/daas_py_api_facility) - Django Facility API (Main)

### [daas_py_idx](https://github.com/nealrout/daas_py_idx) - Generic Index manager - (Main).

### [daas_py_common](https://github.com/nealrout/daas_py_common) - Common Utils

### [daas_py_config](https://github.com/nealrout/daas_py_config) - Configuration & Secret Management

### [daas_solr](https://github.com/nealrout/daas_solr) - SOLR instance setup

### [daas_build](https://github.com/nealrout/daas_build) - Docker and other build/deploy stuff

## Architecture
![My Project Logo](daas_arch_high.png)

## Contact
Neal Routson  
nroutson@gmail.com
