# daas_docs

## Description

Single repository  to aggregate all documentation of projects related to DaaS (Data as a Service).  This overall projects is to dimonstrate a small platform to centralize data, and have it avaialble through an api layer.  It will consist of several source databases, and a SOLR instance for caching.

__daas_py_api_facility__ is setup as a full Django application including ORM.  
__daas_py_api_asset__ is setup as a custom more granular project with a managed DBMS layer.

The idea is to have multple "choices" and models that could be used as boilerplate.

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

__Common components:__  
Logging: Python standarrd logger  
Configuration:  dynaconf  
Secrets: dynaconf/cryptography

## High level project structure

    daas_py                      (ROOT)
    ├───daas_py_api_facility     (FACILITY API)
    │   ├───facility_api         
    │   │   ├───facility         
    │   │   ├───facility_api      
    ├───daas_py_api_asset        (ASSET API)
    │   ├───asset_api            
    │   │   ├───asset            
    │   │   ├───asset_api        
    ├───daas_py_common           (COMMON)
    │   ├───util                 
    ├───daas_py_config           (CONFIG)

## Project Links
### [daas_db](https://github.com/nealrout/daas_db) - PostgreSQL Liquibase

### [daas_py_api_facility](https://github.com/nealrout/daas_py_api_facility) - Django Facility API (Main)

### [daas_py_api_asset](https://github.com/nealrout/daas_py_api_asset) - Django Asset API (Main)

### [daas_py_common](https://github.com/nealrout/daas_py_common) - Common Utils

### [daas_py_config](https://github.com/nealrout/daas_py_config) - Configuration & Secret Management

### [daas_solr](https://github.com/nealrout/daas_solr) - SOLR instance setup

### [daas_py_idx_asset](https://github.com/nealrout/daas_py_idx_asset) - Index manager - asset.

## Architecture
![My Project Logo](daas_arch_high.png)

## Contact
Neal Routson  
nroutson@gmail.com
