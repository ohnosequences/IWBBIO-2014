Next Generation Sequencing (NGS) has definitely reshaped the genomics and transcriptomics scenarios allowing high throughput approaches. Thus biological data analysis demands, more than ever, high performance computing approaches. Cloud computing provides a perfect framework for analyzing this kind of data which is inherently parallel. It allows deploying architectures with as much computing capacity as needed scaling in an horizontal way, being also able to scale down adjusting to the computing needs real time.

Resources configuration is a key point in the cloud computing architecture deploy, even more in the case of bioinformatics analysis where it is pretty often that the tools to use depend on other tools that depend on some other tools and so on. As for high throughput analysis, where a lot resources are to be used and paid for, it is highly recommended to have a robust configuration system to rely on. Knowing beforehand that all the resources to be used are properly configured is invaluable as has been already demonstrated by pioneering efforts such as Galaxy or CloudBioLinux. 

Statika (http://ohnosequences.com/statika) aims to be a basic tool for the declaration and deployment of composable, versioned and reproducible cloud infrastructures for the bioinformatics space. 

Data, tools and infrastructure are treated on an equal footing, and a expressive domain specific language allows the user to express complex dependency relationships, check for possible version conflicts and automatically choose a safe resource creation order. 

By making use of advanced features of the Scala programming language such as dependent types and type-level computations a great deal of structure can be expressed abstractly, and checked at compile time before any cost is incurred. A strong versioning system where both data and tools are included makes reproducibility not only possible but actually enforced. 

Statika has been put to work on scenarios as different as a cloud-based system for scaling inherently parallel computations in the bioinformatics domain: Nispero, or by providing versioned and modular automated deployments of Bio4j, a graph database integrating all data from key resources in the bioinformatics data space, including: UniProt, Gene Ontology, the NCBI Taxonomy or UniRef. 

Statika is open source, available under the AGPLv3 license. 

This project is funded in part by the ITN FP7 project INTERCROSSING (Grant 289974). 
