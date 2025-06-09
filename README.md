# fhir-rdf-validation

This repository contains information and files from work to validate FHIR RDF resources.

### INTRODUCTION

The following instructions and notes are shared to assist people wanting to confirm that the FHIR RDF resources used for any project conform to the HL7 FHIR RDF standard for FHIR data resource types.  

The tool used here to programmatically confirm and validate FHIR RDF resources is the [ShEx.js tool](https://github.com/shexjs/shex.js). 

### GENERAL INSTRUCTIONS

We documented and followed a consistent process to validate instances of the HL7 FHIR RDF data types.  

We used this process to validate instances of FHIR RDF Provenance and Observation resources. 

Example FHIR RDF Provenance and Observation resources are available in this repository in the [examples folder](https://github.com/kgrid/fhir-rdf-validation/tree/main/examples).

In general, the validation process involves first implementing a software tool like ShEx.js for FHIR RDF resource validation, and then running the tool to identify any errors in the structure of the FHIR RDF resources of interest.

### STEP BY STEP PROCEDURE

The steps of this specific technical FHIR RDF data resource validation process are below. 

<1> Clone ShEx.js from its GitHub repository and Install ShEx.js

<2> Initiate the ShEx.js server

<3> Load the ShEx.js server with [HL7 FHIR RDF Shape Expression Schemas](https://github.com/fhircat/ShExValidation) with the needed resource validation constraints.  We used the [R5Plus schemas](https://github.com/fhircat/ShExValidation/tree/main/fhir_rdf_validation/ShExSchemas/R5Plus) provided in the fhircat repo.

<4> Load a text file with the HL7 FHIR RDF Resource to be validated in TTL format. Two example text files are included in this github repository.

<5> Validate the Resource via a call to the ShEx server by using the following technical steps and commands.

After Downloading ShEx.js

- A:  Set PATH for your machine

export PATH="$PATH:/…/shex.js/packages/shex-cli/bin"

- B:  Load the ShEx files using the Validate command

validate --human -x /…/ShExValidation/fhir_rdf_validation/ShExSchemas/R5Plus/Organization.shex --diagnose -S http://localhost:8088/validate

- C:  Use a CURL command like the one below to validate your FHIR RDF resources of interest

curl -i http://localhost:8088/validate -F "data=@/usr/local/miserver/shexdir/tests/obs_test_fault_1.ttl"  -F "queryMap={FOCUS fhir:nodeRole fhir:treeRoot}@<Observation>"


### NOTES

FOR MORE INFORMATION ABOUT ShEx VALIDATION, SEE:

[ShEx webpage](https://shex.io/) 

[Relevant publication](https://pmc.ncbi.nlm.nih.gov/articles/PMC10841909/) 
