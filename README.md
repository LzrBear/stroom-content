# Stroom Content

_Stroom Content_ is a repository of the content definition files used to import entities into _Stroom_. Entities are such things as XML Schemas, XSLT translations, data splitter definitions, pipelines, dashboards, visualisations, etc. This repository provides a means to share common _Stroom_ content in a form that can be imported into multiple instances of _Stroom_.

The content is grouped into a number of _content packs_ which can each be built into a zip file that is ready for import directly into _Stroom_.

## Content pack contents

The following content packs are currently available.  Click on the link for details of what is in each content pack.

### [**core-xml-schemas**](./docs/core-xml-schemas.md) 

The core XML Schemas required by Stroom for basic operation.

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v1.0](https://github.com/gchq/stroom-content/releases/tag/core-xml-schemas-v1.0)                   | Y              | Y             |


### [**event-logging-xml-schema**](./docs/event-logging-xml-schema.md) 

An XML Schema standard for describing audit events.

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v1.0](https://github.com/gchq/stroom-content/releases/tag/event-logging-xml-schema-v1.0)           | Y              | Y             |


### [**internal-dashboards**](./docs/internal-dashboards.md) 

A set of _Dashboard_ entities for displaying various metrics about the state of the _Stroom_ application and the undelying hardware and file systems.

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v1.1](https://github.com/gchq/stroom-content/releases/tag/internal-dashboards-v1.1)                | Y              | Y             |
| [v1.0](https://github.com/gchq/stroom-content/releases/tag/internal-dashboards-v1.0)                | Y              | Y             |


### [**internal-statistics-sql**](./docs/internal-statistics.md) 

A set of _StatisticStore_ entities for representing the internal statistics generated by Stroom and record by the SQL Statistics service. This pack was previously known as 'internal-statistics' so the versions in the matrix below refer to either name.

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v2.0](https://github.com/gchq/stroom-content/releases/tag/internal-statistics-sql-v2.0)            | N              | Y             |
| [v1.2](https://github.com/gchq/stroom-content/releases/tag/internal-statistics-v1.2)                | Y              | N             |
| [v1.1](https://github.com/gchq/stroom-content/releases/tag/internal-statistics-v1.1)                | Y              | N             |
| [v1.0](https://github.com/gchq/stroom-content/releases/tag/internal-statistics-v1.0)                | Y              | N             |


### [**internal-statistics-stroom-stats**](./docs/internal-statistics.md) 

A set of _StroomStatsStore_ entities for representing the internal statistics generated by Stroom and recorded by the Stroom-Stats service.

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v2.0](https://github.com/gchq/stroom-content/releases/tag/internal-statistics-stroom-stats-v2.0)   | N              | Y             |


### [**stroom-101**](./docs/stroom-101.md) 

The entities used in the [quick start guide](https://gchq.github.io/stroom-docs/quick-start-guide/quick-start.html) 

#### Compatibility matrix

| Pack version                                                                                        | Stroom 5.0.x   | Stroom 6.0.x  |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- |
| [v1.0](https://github.com/gchq/stroom-content/releases/tag/stroom-101-v1.0)                         | Y              | Y             |

## Building the content packs

Each content pack is defined as a directory within _stroom-content-source_ with the name of content pack being the name of the directory.

The content packs can be built into the zip files by running the python script _buildContentPacks.py_. You can either build all packs or a list of named packs and you can choose to have them packaged as single combined zip or one per pack.

For example:

```bash
#build all packs into a single zip
./buildContentPacks.py --combine --all 

#build all packs, one zip per pack
./buildContentPacks.py  --all 

#build a named list of packs
./buildContentPacks.py  stroom-101 core-xml-schemas
```

## Released content packs

For a set of pre-built content packs see the [releases page](https://github.com/gchq/stroom-content/releases).

## Importing the content packs

The content pack zip files can be imported into _Stroom_ by selecting _Import_ from the _Tools_ menu.

## A word about UUIDs

Each _Stroom_ entity is identified by a [Universally Unique Identifier](https://en.wikipedia.org/wiki/Universally_unique_identifier).  Where entities have dependencies on other entities, e.g. a _Dashboard_ entity depends on a _StatisticStore_ entity, this dependency relationship is defined by the UUID of the dependency entity. It is possible to import content into _Stroom_ with missing dependencies as this can sometimes be a valid use case, though with missing dependencies the entities will not work correctly until the dependencies are resolved, e.g. by updating the dependency.

All the entities deinfed in these content packs are defined with hard coded UUIDs and dependencies.  It is therefore critical that the correct UUIDs are used in the entity and dependency definitions in the XML.
