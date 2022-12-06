# OntCatOWL-Dataset

Dataset with results of OntCatOWL tests performed on the OntoUML/UFO Catalog.

# Description

The OntCatOWL-Dataset is composed of files with results of [OntCatOWL](https://github.com/unibz-core/OntCatOWL) tests performed via the [OntCatOWL-Tester](https://github.com/unibz-core/OntCatOWL-Tester) on the [OntoUML/UFO Catalog](https://github.com/unibz-core/OntCatOWL).

The FAIR Model Catalog for Ontology-Driven Conceptual Modeling Research, short-named OntoUML/UFO Catalog, is a structured and open-source catalog that contains OntoUML and UFO ontology models. The catalog was conceived to allow collaborative work and to be easily accessible to all its users. Its goal is to support empirical research in OntoUML and UFO, as well as for the general conceptual modeling area, by providing high-quality curated, structured, and machine-processable data on why, where, and how different modeling approaches are used. The catalog offers a diverse collection of conceptual models, created by modelers with varying modeling skills, for a range of domains, and for different purposes.

The tests were performed using the automation tool named [OntCatOWL-Tester](https://github.com/unibz-core/OntCatOWL-Tester), which runs over OntCatOWL. OntCatOWL is the abbreviated name for Identification of Ontological Categories for OWL Ontologies, a software that aims to support the semi-automatic semantic improvement of lightweight web ontologies. We aim to reach the referred semantic improvement via the association of [gUFO](https://nemo-ufes.github.io/gufo/)—a lightweight implementation of the [Unified Foundational Ontology (UFO)](https://nemo.inf.ufes.br/wp-content/uploads/ufo_unified_foundational_ontology_2021.pdf)—concepts to the OWL entities. The aim of gUFO is "_to provide a lightweight implementation of the Unified Foundational Ontology (UFO) suitable for Semantic Web OWL 2 DL applications_".

This document presents the structure of the files generated during the OntCatOWL-Tester execution. For a complete comprehension of the tests (regarding scope, objectives, implementation, etc.), please refer to the OntCatOWL-Tester [description file](https://github.com/unibz-core/OntCatOWL-Tester#readme).

# Contents

- [OntCatOWL-Dataset](#ontcatowl-dataset)
- [Description](#description)
- [Contents](#contents)
- [Build Generated Files](#build-generated-files)
  - [Taxonomical Graph File (taxonomy\_X.ttl)](#taxonomical-graph-file-taxonomy_xttl)
  - [Taxonomical Graph Information File (classes\_data\_Y.csv)](#taxonomical-graph-information-file-classes_data_ycsv)
- [Tests - Generated Files, Descriptions and Results](#tests---generated-files-descriptions-and-results)
- [Contributors](#contributors)
- [Acknowledgements](#acknowledgements)

# Build Generated Files

The OntCatOWL-Tester creates a directory for each one of the catalog's datasets that are tested. Each directory contains other folders with the results of the tests that were performed, but they also contain two different files generated by the OntCatOWL-Tester to be used as input for the tests. For generating these files, the Tester decomposes the original taxonomy from a dataset in its (possibly multiple) independent taxonomies (isolated group of classes related via specialization/generalization relations between each other). We here described each one of these two files: the `taxonomy_X.ttl` and `the classes_data_Y.csv` files.

## Taxonomical Graph File (taxonomy\_X.ttl)

Each `taxonomy_X.ttl` file (with X ranging from 01 to the number of independent taxonomies available in the dataset's OntoUML model) contains an isolated taxonomical graph in OWL (in turtle syntax) got from the OWL taxonomy provided in the catalog's dataset to be tested.

For instance, a single model that has two not connected hierarchical structures of concepts will generate two files: _taxonomy\_01.ttl_ and _taxonomy\_02.ttl_. Each file contains only the following properties: `rdfs:subClassOf`, `owl:Class`, and `rdf:type`.

For generating the URIs, the OntCatOWL-Tester uses the following namespace: *http://taxonomy.model/*

## Taxonomical Graph Information File (classes\_data\_Y.csv)

Each `classes_data_Y.csv` file (with Y ranging from 01 to the number of independent taxonomies available in the dataset's OntoUML model) contains information about all the classes that are part of the taxonomical graph with the corresponding number (i.e., the file _classes\_data\_01.csv_ refers to the taxonomy saved in the file _taxonomy\_01.ttl_). The difference between the results of a test and the inputted data should use this file, as it contains the source data.

The generated csv file contains the following columns:

- `class_name`: name of the OntoUML class as it is in the original model (i.e., without namespace)
- `stereotype_original`: the class's OntoUML stereotype as was attributed by its modeler
- `stereotype_gufo`: the class's OntoUML stereotype mapped to a gUFO endurant type **(click here for more information—link to be created)**
- `is_root`: Boolean value that shows if the class is a root node in the taxonomical graph (i.e., if it has no superclasses)
- `is_leaf`: Boolean value that shows if the class is a leaf node in the taxonomical graph (i.e., if it has no subclasses)
- `is_intermediate`: Boolean value that shows if the class is an intermediate node in the taxonomical graph (i.e., if it has subclasses and superclasses)
- `number_superclasses`: the sum of the number of all direct and indirect superclasses that the class have
- `number_subclasses`: the sum of the number of all direct and indirect subclasses that the class have

As every class must be a root, a leaf, or an intermediate node, note that this file would be inconsistent if:

- is\_root OR is\_leaf OR is\_intermediate != True, or if
- is\_root AND is\_leaf AND is\_intermediate != False

# Tests - Generated Files, Descriptions and Results

Currently, datasets generated from the execution of two tests are available. Please use the following links for accessing the tests descriptions and results.

- Test 1: single class used as input
  - Description **(link to be created)**
  - Results **(link to be created)**
- Test 2: increasing percentage of classes used as input
  - Description **(link to be created)**
  - Results **(link to be created)**

# Contributors

- PhD. Pedro Paulo Favato Barcelos [[GitHub](https://github.com/pedropaulofb)] [[LinkedIn](https://www.linkedin.com/in/pedropaulofavatobarcelos/)]
- Tiago Prince Sales [[GitHub](https://github.com/tgoprince)] [[LinkedIn](https://www.linkedin.com/in/tiagosales/)]
- Elena Romanenko [[GitHub](https://github.com/mozzherina)] [[LinkedIn](https://www.linkedin.com/in/mozzherina/)]
- Prof. PhD. Giancarlo Guizzardi [[LinkedIn](https://www.linkedin.com/in/giancarloguizzardibb51aa75/)]
- Eng. MSc. Gal Engelberg [[GitHub](https://github.com/GalEngelberg)] [[LinkedIn](https://www.linkedin.com/in/galengelberg/)]
- Eng. MSc. Dan Klein [[GitHub](https://github.com/danklein10)] [[LinkedIn](https://www.linkedin.com/in/~danklein/)]

# Acknowledgements

This work is a collaboration between the Free University of Bozen-Bolzano, the University of Twente, and Accenture Israel Cybersecurity Labs.