# Test 1 Files

## Description

This document describes the structure of the files generated by the execution of Scior Test 1. Each section below regards a different type of file. The nomenclatures' definitions of the files presented here can be accessed [in this link](https://github.com/unibz-core/Scior-Dataset#nomenclature-of-files-and-folders). For a complete description of Test 1, please access [this link](https://github.com/unibz-core/Scior-Tester/blob/main/documentation/Scior-Tester-Test1.md).

Test 1 was executed in both complete and incomplete Scior modes (more information about the Scior execution modes are presented in [this link](https://github.com/unibz-core/Scior/blob/main/documentation/Scior-Execution-Modes.md)), generating the content presented in two folders inside each one of the catalog's datasets: tt001_ac and tt001_an, respectively. These folders contain the same type of documents here described, but with the different content that resulted from the different execution modes.

## Contents

- [Execution Summary _csv_ Files](#execution-summary-csv-files)
- [Execution Statistics _csv_ Files](#execution-statistics-csv-files)
  - [Classes](#classes)
    - [List of Items](#list-of-items)
  - [Classifications](#classifications)
    - [List of Items](#list-of-items-1)
  - [Other Items](#other-items)
- [Execution Times _csv_ Files](#execution-times-csv-files)
- [Settings _csv_ Files](#settings-csv-files)
- [Inconsistencies _csv_ Files](#inconsistencies-csv-files)
- [Results _yaml_ Files](#results-yaml-files)
- [Results _csv_ Files](#results-csv-files)
- [Knowledge Matrix _csv_ Files](#knowledge-matrix-csv-files)
- [Divergences _csv_ Files](#divergences-csv-files)

## Execution Summary _csv_ Files

The execution summary registers the input class and its classification used in each one of the Scior executions performed on the model's taxonomies.

A file entitled `summary_XXX_tt001_MM_txYYY.csv` is generated for each model and it aggregates information about all the Scior executions on the same taxonomy.

For this file and for the description of the next ones in this document, XXX corresponds to the name of the dataset being tested, tt001 refers to Test 1, MM refers to the test parameters (e.g., ac or an for Test 1), and YYY corresponds to the taxonomy number. As an example, the file _summary_aguiar2018rdbs-o_tt001_an_tx001.csv_ inside a dataset's folder corresponds to the taxonomy file _aguiar2018rdbs-o_tx001.ttl_). The items registered in the _csv_ files are:

- `execution_number`: is the first column of the _csv_ file. Registers the number of the execution of the test in which the next fields were measured or calculated
- `input_class_name`: name of the model's class used as input for performing the execution of Scior
- `input_class_stereotype`: "stereotype" of input class. This information is, in fact, a gUFO classification got via a mapping from the original OntoUML stereotype of the class. More information can be found [in this link](https://github.com/unibz-core/Scior-Tester/blob/main/documentation/Scior-Tester-Build.md#ontouml-stereotype-and-gufo-classification).

## Execution Statistics _csv_ Files

This file registers statistics related to numbers and percentages of classes, classifications, and other information got from the software execution.

For an easier presentation, we are going to classify the data presented in this file into three groups: classes, classifications, and others. Note that the order of the items being described does not correspond to the same order they occur in the _csv_ file.

A single file entitled `statistics_XXX_tt001_MM_txYYY.csv` is generated for each model's independent taxonomical graph and it aggregates information about all its Scior executions (e.g., _statistics_aguiar2018rdbs-o_tt001_an_tx001.csv_).

### Classes

Classes items (i.e., csv header columns) always have the term "classes_". The different measured or calculated aspects are:

- Measuring moments: before ("_b"), after ("_a"), and difference (prefix "diff") between the measuring moments
- Knowledge about a class classification: totally unknown ("_tu"), partially known ("_pk"), totally known ("_tk")
- Data format: measured values (suffix "_v") (i.e., units), and percentages (suffix "_p")

#### List of Items

- `classes_b_total_classes_number`: total number of classes in the file `taxonomy_N.ttl` used in the software before the execution of Scior rules
  - As no class is included or excluded during the execution of the software, classes_b_total_classes_number = classes_a_total_classes_number
- `classes_b_tu_classes_types_v`: number of classes with no information about their classifications (i.e., totally unknown classes) before the Scior execution
- `classes_b_pk_classes_types_v`: number of classes with partial information known about their classifications (i.e., partially known classes) before the Scior execution
- `classes_b_tk_classes_types_v`: number of classes with complete information known about their classifications (i.e., totally known classes) before the Scior execution
- `classes_b_tu_classes_types_p`: percentage of totally unknown classes before the Scior execution with relation to the total number of classes
  - Calculation formula: classes_b_tu_classes_types_p = classes_b_tu_classes_types_v/classes_b_total_classes_number
- `classes_b_pk_classes_types_p`: percentage of partially known classes before the Scior execution with relation to the total number of classes
  - Calculation formula: classes_b_pk_classes_types_p = classes_b_pk_classes_types_v/classes_b_total_classes_number
- `classes_b_tk_classes_types_p`: percentage of totally known classes before the Scior execution with relation to the total number of classes
  - Calculation formula: classes_b_tk_classes_types_p = classes_b_tk_classes_types_v/classes_b_total_classes_number
- `classes_a_total_classes_number: total number of classes in the file taxonomy.ttl used in the software after the execution of Scior rules. As no class is included or excluded during the execution of the software, classes_b_total_classes_number = classes_a_total_classes_number.
- `classes_a_tu_classes_types_v`: number of classes with no information about their classifications (i.e., totally unknown classes) after the Scior execution
- `classes_a_pk_classes_types_v`: number of classes with partial information known about their classifications (i.e., partially known classes) after the Scior execution
- `classes_a_tk_classes_types_v`: number of classes with complete information known about their classifications (i.e., totally known classes) after the Scior execution
- `classes_a_tu_classes_types_p`: percentage of totally unknown classes after the Scior execution with relation to the total number of classes
  - Calculation formula: classes_a_tu_classes_types_p = classes_a_tu_classes_types_v/classes_a_total_classes_number
- `classes_a_pk_classes_types_p`: percentage of partially known classes after the Scior execution with relation to the total number of classes
  - Calculation formula: classes_a_pk_classes_types_p = classes_a_pk_classes_types_v/classes_a_total_classes_number
- `classes_a_tk_classes_types_p`: percentage of totally known classes after the Scior execution with relation to the total number of classes
  - Calculation formula: classes_a_tk_classes_types_p = classes_a_tk_classes_types_v/classes_a_total_classes_number
- `diff_tu_classes_types_v`: difference (in units) between the number of totally unknown classes before and after the Scior execution
  - Calculation formula: diff_tu_classes_types_v_d = classes_a_tu_classes_types_v classes_b_tu_classes_types_v
- `diff_pk_classes_types_v`: difference (in units) between the number of partially known classes before and after the Scior execution
  - Calculation formula: diff_pk_classes_types_v_d = classes_a_pk_classes_types_v classes_b_pk_classes_types_v
- `diff_tk_classes_types_v`: difference (in units) between the number of totally known classes before and after the Scior execution
  - Calculation formula: diff_tk_classes_types_v_d = classes_a_tk_classes_types_v classes_b_tk_classes_types_v
- `diff_tu_classes_types_p`: difference (in percentage) between the percentage of totally unknown classes before and after the Scior execution
  - Calculation formula: diff_tu_classes_types_p_d = classes_a_tu_classes_types_p classes_b_tu_classes_types_p
- `diff_pk_classes_types_p`: difference (in percentage) between the percentage of partially known classes before and after the Scior execution
  - Calculation formula: diff_pk_classes_types_p_d = classes_a_pk_classes_types_p classes_b_pk_classes_types_p
- `diff_tk_classes_types_p`: difference (in percentage) between the percentage of totally known classes before and after the Scior execution
  - Calculation formula: diff_tk_classes_types_p_d = classes_a_tk_classes_types_p classes_b_tk_classes_types_p

### Classifications

Classifications are the gUFO classes (e.g., Kind, Sortal, RigidType) in which an OWL ontology concept can be mapped to (for endurant types, via a rdf:type predicate). Considering only Endurant Types, the possible classifications of a class are: `gufo:AntiRigidType`, `gufo:Category`, `gufo:Kind`, `gufo:Mixin`, `gufo:NonRigidType`, `gufo:NonSortal`, `gufo:Phase`, `gufo:PhaseMixin`, `gufo:RigidType`, `gufo:Role`, `gufo:RoleMixin`, `gufo:SemiRigidType`, `gufo:Sortal`, `gufo:SubKind`.

Classifications items always have the term "classif_". The different measured or calculated aspects are:

- Measuring moments: before ("_b"), after ("_a"), and difference (prefix "diff_" and suffix "_d") between the measuring moments
- Knowledge about classifications: total number, known, and unknown classifications. The total number is the sum of known and unknown classifications
- Data format: measured values (suffix "_v") (i.e., units), and percentages (suffix "_p")

#### List of Items

- `classif_b_total_classif_types_v`: total number of classifications available for all the classes in the file taxonomy.ttl used in the software before the execution of Scior rules. The total number of classifications is the number of classifications available for a single class multiplied by the number of classes in the model. As no classification is included or excluded during the execution of the software, classif_b_total_classif_types_v = classif_a_total_classif_types_v. Also, classif_b_total_classif_types_v = classif_b_unknown_classif_types_v + classif_b_known_classif_types_v.
- `classif_b_unknown_classif_types_v`: is the sum of all unknown classifications of all classes before the execution of Scior rules
- `classif_b_known_classif_types_v`: is the sum of all known classifications of all classes before the execution of Scior rules
- `classif_a_total_classif_types_v`: total number of classifications available for the classes in the file taxonomy.ttl used in the software after the execution of Scior rules. The total number of classifications is the number of classifications available for a single class multiplied by the number of classes in the model. As no classification is included or excluded during the execution of the software, classif_b_total_classif_types_v = classif_a_total_classif_types_v. Also, classif_a_total_classif_types_v = classif_a_unknown_classif_types_v + classif_a_known_classif_types_v.
- `classif_a_unknown_classif_types_v`: is the sum of all unknown classifications of all classes after the execution of Scior rules
- `classif_a_known_classif_types_v`: is the sum of all known classifications of all classes after the execution of Scior rules
- `classif_b_unknown_classif_types_p`: percentage of unknown classification types before the Scior execution in relation to the quantity of all classifications
  - Calculation formula: classif_b_unknown_classif_types_p = classif_b_unknown_classif_types_v/classif_b_total_classif_types_v
- `classif_b_known_classif_types_p`: percentage of known classification types before the Scior execution in relation to the quantity of all classifications
  - Calculation formula: classif_b_known_classif_types_p = classif_b_known_classif_types_v/classif_b_total_classif_types_v
- `classif_a_unknown_classif_types_p`: percentage of unknown classification types after the Scior execution in relation to the quantity of all classifications
  - Calculation formula: classif_a_unknown_classif_types_p = classif_a_unknown_classif_types_v/classif_a_total_classif_types_v
- `classif_a_known_classif_types_p`: percentage of known classification types after the Scior execution in relation to the quantity of all classifications
  - Calculation formula: classif_a_known_classif_types_p = classif_a_known_classif_types_v/classif_a_total_classif_types_v.
- `diff_unknown_classif_types_v`: difference in units between the quantity of unknown classification types before and after the Scior execution
  - Calculation formula: diff_unknown_classif_types_v_d = classif_a_unknown_classif_types_v classif_b_unknown_classif_types_v
- `diff_known_classif_types_v`: difference in units between the quantity of known classification types before and after the Scior execution
  - Calculation formula: diff_known_classif_types_v_d = classif_a_known_classif_types_v classif_b_known_classif_types_v
- `diff_unknown_classif_types_p`: difference in percentage between the quantity of unknown classification types before and after the Scior execution
  - Calculation formula: diff_unknown_classif_types_p_d = classif_a_unknown_classif_types_p classif_b_unknown_classif_types_p
- `diff_known_classif_types_p`: difference in percentage between the quantity of known classification types before and after the Scior execution
  - Calculation formula: diff_known_classif_types_p_d = classif_a_known_classif_types_p classif_b_known_classif_types_p

### Other Items

Besides information about classes and their classifications, the _csv_ file also presents two additional fields:

- `execution`: is the first column of the _csv_ file. Registers the number of the execution of the test in which the next fields were measured or calculated
- `incomplete_classes_found`: is the last column of the _csv_ file. Registers how many incomplete classes Scior identified during the execution

## Execution Times _csv_ Files

This file registers the time (in seconds) that each individual rule took for being performed and the execution total time.

A single file entitled `times_XXX_tt001_MM_txYYY.csv` is generated for each model's independent taxonomical graph and it aggregates information about all its Scior executions (e.g., _times_aguiar2018rdbs-o_tt001_an_tx001.csv_).

The items registered in the _csv_ files are:

- `execution`: is the first column of the _csv_ file. Registers the number of the execution of the test in which the next fields were measured or calculated
- `k_s_sup`: execution time in seconds for the specific Scior rule of the same name
- `s_k_sub`: execution time in seconds for the specific Scior rule of the same name
- `t_k_sup`: execution time in seconds for the specific Scior rule of the same name
- `ns_s_sup`: execution time in seconds for the specific Scior rule of the same name
- `s_ns_sub`: execution time in seconds for the specific Scior rule of the same name
- `r_ar_sup`: execution time in seconds for the specific Scior rule of the same name
- `ar_r_sub`: execution time in seconds for the specific Scior rule of the same name
- `ns_sub_r`: execution time in seconds for the specific Scior rule of the same name
- `ks_sf_in`: execution time in seconds for the specific Scior rule of the same name
- `n_r_t`: execution time in seconds for the specific Scior rule of the same name
- `ns_s_spe`: execution time in seconds for the specific Scior rule of the same name
- `nk_k_sup`: execution time in seconds for the specific Scior rule of the same name
- `s_nsup_k`: execution time in seconds for the specific Scior rule of the same name
- `sub_r_r`: execution time in seconds for the specific Scior rule of the same name
- `nrs_ns_r`: execution time in seconds for the specific Scior rule of the same name
- `total_time`: the sum of the execution times of all fourteen rules implemented in Scior. I.e., the sum of all other items registered in this file (except for the item "execution"

For the description of each execution rule implemented in the Scior, please access [this link](https://github.com/unibz-core/Scior/blob/main/documentation/Scior-ImplementedRules.md).

## Settings _csv_ Files

This file registers the information about the hardware and software used for executing the same test in all taxonomies of the dataset.

A single file entitled `settings_XXX_tt001_MM.csv` is generated once for each model's (e.g., _settings_aguiar2018rdbs-o_tt001_an.csv_).

The items registered in the _csv_ files are:

- `scior_version`: Scior version used for executing the software
- `python_version`: Python version used for executing the software
  - Printed_string = _platform.python_version()_
- `operating_system`: Operating System of the computer in which the Tester was executed
  - printed string = _platform.system() + " " + platform.release() + " - v" + platform.version()_
- `processor`: Processor of the computer in which the Tester was executed
  - printed string = _platform.processor() + " (" + platform.machine() + ")"_
- `installed_ram`: Amount of RAM memory (in GB) on the computer in which the Tester was executed
  - printed_string = _str(round(psutil.virtual_memory().total / (1024.0 ** 3)))_

Considering that this file is created only once for each test in a dataset, it will always have only two lines: a first one with the headers and the second one with values.

## Inconsistencies _csv_ Files

Considering an incomplete model as complete may cause inconsistencies—and the catalog models used for this test don't explicitly state if they intend to represent complete or incomplete information. Hence, the execution of Test 1 AC resulted in the detection of inconsistencies in some models. Inconsistencies may also occur when an OntoUML model is syntactically invalid. However, Test 1 cannot detect this situation as it only uses a single class as input.

As an overview of each dataset contains inconsistencies, Test 1 report all inconsistencies found in the file `inconsistencies_tt001_MM.csv`  (e.g., _inconsistencies_tt001_ac.csv_).

The _csv_ file contains the following columns:

- `taxonomy_name`: a string representing name of the taxonomy file in which the inconsistency was detected.
- `execution_number`: is the first column of the _csv_ file. Registers the number of the execution of the test in which the inconsistency was detected
- `inconsistent_class_name`: the model's class used as input on the test in which the inconsistency was detected
- `inconsistent_class_classification`: the input class's gUFO classification (i.e., its OntoUML stereotype mapped to a gUFO endurant type)

The Scior-Tester creates this file only if Test 1 detects at least one inconsistency in a dataset during its execution. If created, only one file is created for each test. I.e., a single file is going to be created in the `catalog/` folder.

## Results _yaml_ Files

Differently from the other files already presented, Test 1 generates the _csv_ and _yaml_ results files for each of its executions (i.e., the number of these files is going to be the same number of classes that the tested model has). The Tester stores these files in the `results` folder inside the catalog's dataset folder.

This _yaml_ file contains the complete output of the execution of the Scior. It presents the results of all evaluated classes, displaying their following information in a dictionary format:

- `input`: a Boolean value that indicates if the class was used as an input for the execution of the test
- `is_type`: a list of all gUFO classifications asserted to the class
- `can_type`: a list of all gUFO classifications that a class _can_ assume (i.e., it is not possible to assume that the class can be classified according to an item on the list and also there are no known restrictions against its classification
- `not_type`: a list of all gUFO classifications that the class cannot assume
- `is_incomplete`: a Boolean value that indicates if Scior detected the class as incomplete or not
- `detected_in`: a list containing all rules that detected the incompleteness of the class. If the value of is_incomplete is False, then this list must be empty

This file is generated according to the pattern `complete_XXX_tt001_MM_txYYY_exZZZ.yaml` (e.g., _complete_aguiar2018rdbs-o_tt001_an_tx001_ex001.yaml_, for the first execution of the taxonomy 001 of the dataset aguiar2018rdbs-o).

## Results _csv_ Files

As occurs with the results _yaml_ files, Test 1 generates the _csv_ results files for each of its executions (i.e., the number of these files is going to be the same number of classes that the tested model has). The Tester stores these files in the `results` folder inside the catalog's dataset folder.

This file contains a simplified view of the results presented in the _yaml_ file with the objective of simplifying queries for evaluating possible divergences between the expected and the effective result (i.e., between the original categorization of the class, as provided by the author, and the result of the Scior execution). Divergences occur if any class has the value "not" in its _classification_final_list_ field. There is a match between the expected value and the execution result when this field has the value "is". The field's value "can" does not represent a match nor a divergence.

- `class_name`: name of the class being evaluated
- `class_original_classification`: original gUFO classification of the class, obtained from its OntoUML stereotype
- `classification_final_list`: list where the class's original gUFO classification is located after the Scior execution

This file is generated according to the pattern `simple_XXX_tt001_MM_txYYY_exZZZ.csv` (e.g., _simple_aguiar2018rdbs-o_tt001_an_tx001_ex001.csv_, for the first execution of the taxonomy 001 of the dataset aguiar2018rdbs-o).

## Knowledge Matrix _csv_ Files

Test 1 generates a _csv_ file containing the knowledge matrix for each of its executions (i.e., for Test 1, the number of these files is going to be the same number of classes that the tested model has). The Tester stores these files in the `results` folder inside the catalog’s dataset folder.

The Knowledge Matrix _csv_ File contains a matrix of integers of size 15x15, without headers for columns and for rows. The user must interpret the values in this file according to the Scior’s knowledge matrix [documentation](https://github.com/unibz-core/Scior/blob/main/documentation/Scior-Functioning.md#report-file).

Scior generates this file according to the pattern `matrix_XXX_tt001_MM_txYYY_exZZZ.csv` (e.g., _matrix_aguiar2018rdbs-o_tt001_an_tx001_ex001.csv_, for the first execution of the taxonomy 001 of the dataset aguiar2018rdbs-o).

## Divergences _csv_ Files

Considering the definition of divergence presented in this documentation ([click here](#results-csv-files)), this file presents a list of all taxonomies in the catalog that presented divergences and the corresponding result file that registers this divergence.

- `taxonomy_name`: a string representing the name of the taxonomy file in which the divergence was found.
- `result_file`: a string representing the name of the results _csv_ file that registers the divergence.

In simple terms, every time that a Result *csv * file has the value "not" in its column `classification_final_list`, this file and the corresponding taxonomy are going to be here reported.

This file is created only in the case that at least one divergency is found (considering the software execution in all datasets). A single file is created in the `catalog/` folder for each test, having the name `divergences_tt001_MM.csv` (e.g., *divergences_tt001_ac.csv*).
