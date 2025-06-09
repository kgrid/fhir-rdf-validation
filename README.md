# fhir-rdf-validation
This repository contains information and files from work to validate FHIR RDF resources.

We documented and followed a consistent process to validate instances of the HL7 FHIR RDF Provenance and Observation resources. 

The steps of this technical process are below. 

Technical Steps to Validate HL7 FHIR RDF Resources

<1> Clone ShEx.js from its GitHub repository and Install ShEx.js

<2> Initiate the ShEx.js server

<3> Load the ShEx.js server with HL7 FHIR RDF Shape Expression Schemas35 with the needed resource validation constraints

<4> Load a text file with the HL7 FHIR RDF Resource to be validated in TTL format

<5> Validate the Resource via an API call to the ShEx server

More information is available in the document titled ____
