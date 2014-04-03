% Bio4j: bigger, faster, leaner
% Pablo Pareja-Tobes
% 08.04.2014

# Introduction

----

### What is Bio4j?

**Bio4j** is a bioinformatics _graph_-based data platform **integrating** the most representative **open data sources** around **protein information** available today.

\  
\ 

### Why Bio4j?

Bio Data **+** Graph Databases **+** The Cloud

----

### Data sources
 
+-----------------------------------------------------------+------------------------------------------------------------------------------+
|                                                           |                                                                              |
+===========================================================+==============================================================================+
|                                                           | * *[UniProt KB](http://www.uniprot.org/help/uniprotkb)* (SwissProt + Trembl) |
|                                                           | * *[Gene Ontology](http://www.geneontology.org/)* (GO)                       |
| <img width="400" src="resources/images/data-sources.jpg"> | * *[UniRef](http://www.uniprot.org/help/uniref)* (50,90,100)                 |
|                                                           | * *[RefSeq](http://www.ncbi.nlm.nih.gov/RefSeq/)*                            |
|                                                           | * *[NCBI taxonomy](http://www.ncbi.nlm.nih.gov/Taxonomy/)*                   |
|                                                           | * *[Expasy Enzyme DB](http://enzyme.expasy.org/)*                            |
+-----------------------------------------------------------+------------------------------------------------------------------------------+

<!-- 
<img width="500" src="resources/images/data-sources.jpg">

* *[UniProt KB](http://www.uniprot.org/help/uniprotkb)* (SwissProt + Trembl)
* *[Gene Ontology](http://www.geneontology.org/)* (GO)
* *[UniRef](http://www.uniprot.org/help/uniref)* (50,90,100)
* *[RefSeq](http://www.ncbi.nlm.nih.gov/RefSeq/)*
* *[NCBI taxonomy](http://www.ncbi.nlm.nih.gov/Taxonomy/)*
* *[Expasy Enzyme DB](http://enzyme.expasy.org/)*
 -->

----

### It's open!

- Code is under the [**AGPLv3**](https://www.gnu.org/licenses/agpl-3.0.html) license
- Only [**Open Data**](http://okfn.org/opendata/) is integrated
- Implementation & release process is [**100% public**](https://github.com/bio4j/bio4j) and totally **transparent**

----

### Biology & Databases today

* Highly **interconnected overlapping** knowledge 
* spread over **different data sources**
* mantained in the **Relational database model** or sometimes even just as plain **CSV files**

\ 

That might be OK for simple scenarios but as the **amount** and **diversity** of data grows, **domain models** become crazily complicated!

----

<img width="800" src="resources/images/tables.jpg">

_Doesn't look very compelling right?_ :)

 
----

### Relational model

With relational paradigm the double implication

**Entity** $\Longleftrightarrow$ **Table**

doesn't go both ways, which implies

* **auxiliary tables**
* **artificial IDs**
* dealing with **raw tables** \
  (in spite of entity-relationship diagrams)

\

**Integrating** new knowledge becomes **difficult**

----

### Biology $\neq$ Table

> * **Life** in general and **biology** in particular  
    are probably not 100% like a graph...
> * but one thing is sure: they _**are not a set of tables!**_

----

### Why graph databases?

* Data is stored in a way that **semantically represents its own structure**
* Incorporating new data is easy $\Rightarrow$ it's **scalable**
* **Vertex-centric** _(local)_ indices allow to overcome the supernode problem

----

<!-- ### Why cloud?

* data as a service
* machine configurations

 -->

<!-- I'm not sure if I should talk about this: -->
### How it all started 

* Need for **massive access** to _Gene Ontology_ annotations
* [**BG7**](http://bg7.ohnosequences.com/) bacterial genome annotation system 
* Need for massive direct access to **protein information**

----

### More and more data!

* As _other_ data sources were becoming a _bottleneck_ they were being added to Bio4j
* First it was Uniprot KB, then Uniref and **we didn't stop yet**

----

### Numbers

* $10^9$ edges
* $2 \times 10^8$ nodes
* $6 \times 10^8$ properties
* $150$ edge types
* $40$ node types

<!-- * **`1,216,993,547`** relationships
* `190,625,351` nodes
* `584,436,429` properties
* `144` relationship types
* `42` node types
 -->
----

### Bio4j structure

Bio4j importing process is **modular** and **customizable** allowing you to import just the data you are interested in.


<!-- Just keep in mind that you must be **coherent**
_e.g. you cannot import protein interactions if you didn't import any protein yet!_
-->
----

### Bio4j APIs

> 1. abstract **domain model**
> 2. **Blueprints** implementation
> 3. **technology-specific** versions

----

### domain model

Bio4j database has a **well-defined** domain model and all nodes and relationships comply with this abstract model

----

![](resources/images/Bio4jDomainModelWithCardinality.jpg)

----

### domain model _why?_

- abstract over Blueprints
- more precise **typing**
- implementations can use technology-specific features

----

### Key advantage

_Different_ **graph topologies** at the storage level, _same_ **domain model**. 

Example: use **type nodes** in _Titan_, **labels** in _Neo4j_.

----

### Blueprints layer

A default **[Blueprints](https://github.com/tinkerpop/blueprints/)** implementation of the abstract model.

----

Apart from the set of interfaces developed as the **first layer** for the _domain model_ there's an **extra layer** that uses _Blueprints_. This way we’re going one step further for making the domain model **independent** from the choice of _database technology_

----

### technology-specific

Optimizations, features, etc.

* **[Neo4j](https://github.com/neo4j/neo4j)** 
* **[Titan](https://github.com/thinkaurelius/titan/)** (WIP)
* **[OrientDB](https://github.com/orientechnologies/orientdb/)** (planned)

----

### why Neo4j

> * wide **adoption**
> * stable
> * **Cypher**

----

### why Titan

> * **local!** indexes
> * **on-disk** access
> * **type** definitions -> _constraints!_

----

### Bio4j and the cloud

* **Interoperability** and data distribution
* **Backup** and **storage**
* **Scalability**
* Applications and service providers on the cloud
* Cost-effective

----

### dev and release process

* coordinate **data** and **code**
* **[Semantic Versioning](http://semver.org/spec/v2.0.0.html)**
* **Cloud** integration, distribution, deployment, ...

----

### how?

- **[Statika](http://ohnosequences/statika)** cloud, data + code, modules (see [next talk](https://fosdem.org/2014/schedule/event/graphdevroom_bio4j_1/))
- **[sbt](https://github.com/sbt/sbt)** build Java + Scala, automated Bio4j-specific test & release
- **[git + github](https://github.com/bio4j)** versioning, docs, collaboration, coordination

----

<br/>
<br/>

<!-- How Bio4j -->
### _how_ to use Bio4j?

use cases, case studies, community

----

### use cases


<!--
----

### ??? and !!!

I don't get what's this... :|
-->

----

### how we use it

* **[bg7](http://bg7.ohnosequences.com)** genome annotation
* **mg7** metagenomics analysis
* comparative genomics, network analysis, genome assembly, ...

----

### case study II

**Ohio State University**

 * **Integration** and **analysis** of Chip-seq data
 * **Modeling** genomic information and **gene regulatory networks**

----

### case study III

**Berkeley Phylogenomics Group**

* Graph database for _Big Data challenges_ in **genomics** developed **on top of Bio4j**

----

### community

* **[\@bio4j](http://twitter.com/bio4j)** twitter
* **[bio4j](https://github.com/bio4j)** github org
* **[bio4j-user](http://groups.google.com/group/bio4j-user)** google group
* **[bio4j](http://www.linkedin.com/groups/Bio4j-3890937)** linkedin

----

<br/>
<br/>

<!-- How Bio4j -->
### _who_'s doing Bio4j?

research group, team

----

### oh no sequences!

**[Era7 bioinformatics](http://era7bioinformatics.com)** R&D group

- **web** -> [ohnosequences.com](http://ohnosequences.com)
- **Github** -> [ohnosequences](https://github.com/ohnosequences)

----

### team

- **[Pablo Pareja](http://ohnosequences.com/ppareja)** <br />
    project leader & main dev
- **[Eduardo Pareja-Tobes](http://ohnosequences.com/eparejatobes)**<br /> 
    technology & architecture
- **[Raquel Tobes](http://ohnosequences.com/rtobes)** <br />
    bio data integration

----

### team

- **[Alexey Alekhin](http://ohnosequences.com/aalekhin)** <br />
    Statika, release process, dev
- **[Marina Manrique](http://ohnosequences.com/mmanrique)** <br />
    bio data integration
- **[Evdokim Kovach](http://ohnosequences.com/ekovach)**<br /> 
    dev
    
----
