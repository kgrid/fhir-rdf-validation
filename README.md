# fhir-rdf-validation

This repository contains information and files from work to validate FHIR RDF resources.

## INTRODUCTION

The following instructions and notes are shared to assist people wanting to confirm that the FHIR RDF resources used for any project conform to the HL7 FHIR RDF standard for FHIR data resource types.  

The tool used here to programmatically confirm and validate FHIR RDF resources is the [ShEx.js tool](https://github.com/shexjs/shex.js). 

## GENERAL INSTRUCTIONS

We documented and followed a consistent process to validate instances of the HL7 FHIR RDF Provenance and Observation resources. 

The steps of this technical process are below. 

Note:  ShEx.js required us first to serialize our FHIR RDF resources in TTL before validating them. 

Technical Steps to Validate HL7 FHIR RDF Resources

<1> Clone ShEx.js from its GitHub repository and Install ShEx.js

<2> Initiate the ShEx.js server

<3> Load the ShEx.js server with HL7 FHIR RDF Shape Expression Schemas35 with the needed resource validation constraints

<4> Load a text file with the HL7 FHIR RDF Resource to be validated in TTL format

<5> Validate the Resource via an API call to the ShEx server

More information is available in the document titled ____


USING ShEx VALIDATOR for FHIR RDF Validation



BEFORE STARTING WITH ShEx VALIDATION, SEE:
https://shex.io/ 
https://github.com/shexjs/shex.js 
https://pmc.ncbi.nlm.nih.gov/articles/PMC10841909/ 

After Downloading ShEx.js

STEP 1:  Set PATH

export PATH="$PATH:/…/shex.js/packages/shex-cli/bin"

STEP 2:  Run Validate Command

validate --human -x /…/ShExValidation/fhir_rdf_validation/ShExSchemas/R5Plus/Organization.shex --diagnose -S http://localhost:8088/validate

STEP 3:  Example of Validating FHIR Data with this Command

curl -i http://localhost:8088/validate 
     
-F "data=@/.../ShExValidation/fhir_rdf_validation/FHIR_RDF_Examples/R5/file_to_be_validated"      

-F 
"queryMap={FOCUS fhir:nodeRole fhir:treeRoot}@<Organization>"


EX: 
curl -i http://localhost:8088/validate -F"data=@/Users/ajf/Desktop/71323f/ShExValidation/fhir_rdf_validation/FHIR_RDF_Examples/R5/account-example.ttl"      
-F"queryMap={FOCUS fhir:nodeRole fhir:treeRoot}@<Account>"

### NOTES
