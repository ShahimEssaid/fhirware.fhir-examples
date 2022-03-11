# Introduction

The goal of this project is to support creating FHIR-based data structures for learning and prototyping purposes. The setup in this project allows a user to prototype their data needs while also getting IDE support for auto completion and validation. This approach is a bottom up approach where use cases are demonstrated by examples without the need to setup a full IG project to accomplish the same goals.

The examples created with this setup can either be proper FHIR Resource instances (based on the official FHIR schemas) or other arbitrary FHIR structures used by those Resource instances (i.e. data types, backbone elements, etc.). 

For now, this project is only configured for use with [Visual Studio Code (VSC)](https://code.visualstudio.com/).

This project is still WIP and is likely to be buggy at times until it's been tested by end users. Please create issues at [the GitHub repository](https://github.com/ShahimEssaid/fhirware.fhir-examples) if you notice any problems or have enhancement ideas.

# Getting started

* Install Visual Studio Code and add the YAML extension from Red Hat.

* Use File -> Open Workspace... to open the `fhir-examples.code-workspace` workspace file at the root of the repository.

# Some minimal documentation

This is the top directory for your example subdirectories. 

* Create a subdirectory named after what you're trying to demonstrate with your example.
* Create a README.md file in your directory to document what you're demonstrating.
* Add additional files as needed.
* For the FHIR and schema supported files, follow the file naming pattern shown below to get the schema support. The schema support, whether for JSON or Yaml, will provide auto complete and validation to the degree the schema has that information. The current schema does not enforce all the validation described in the specification's StructureDefinitions for the various structures. 
    * *_resource_R4*.json to create an R4 FHIR resource in JSON.
    * *_example_R4*.json to create an R4 **Example** in JSON.  See what an **Example** means in the home README.md
    * *_resoruce_R5*.json same but for R5.
    * *_example_r5*.json same but for R5.
* The "R4" and "R5" parts of a file name mean the latest available schema for R4 or R5.  For R4, it is currently 4.0.1 and for R5 it is the build from 2/22/2022.  If you like to pin your files to the more specific version/date, add the following full file name suffix instead of simply R4 or R5:
    * _R4.0.1*.*
    * _R5.2022.02.22*.*
* Use the resource format to create proper FHIR resource examples that you can copy as is to post to a FHIR server.  The example format is useful for creating multiple examples in one file, giving titles and descriptions for each, exploring FHIR structures other than resources, etc.
* If you install the "YAML ❤️ JSON" VS Code extension, you will be able to convert between Yaml and JSON. This might help with writing files in Yaml for better readability but still be able to convert to JSON to submit to a FHIR server.


# The **Example** schema

The \*\_example_\* files support creating arbitrary FHIR structures in JSON or Yaml formats according to this **Example** template.

* A file has a top level object with arbitrary key names. Each key holds an **Example** object

* An **example** object has the following structure. Double quotes are only needed for the JSON format, or if really needed for the Yaml format.

    * A `"Title":` key that holds a string as the title of the example. This field is required.

    * A `"Description":` key that holds an array of strings. Each string in the array can represent a sentence, paragraph, etc.  The array helps break up a lengthy text block into multiple parts. Consider this array as the documentation of the example, the use case, etc.

    * A `"Links":` array of objects that contain `"title":` and `"link":` keys. This array helps with holding links to a GitHub issue, references for the example, etc.  The `"title":` key holds some label or name for the link.

    * A `"Schema":` key. This is an enumeration of the various FHIR structure names for which you can create an example. For example, if you would like to create an example of the CodeableConcept data type, you would use Ctrl+Space to get the suggestions and then type to filter to CodeableConcept.

    * An `"Instance":` key that holds the FHIR instance. It is an instance of the FHIR structure name you selected for the `"Schema":` key.
