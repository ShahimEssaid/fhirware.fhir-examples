# This readme needs to be reviewed and updated. Do not rely of it for now but Shahim can explain as needed.

# Introduction

The goal of this project is to support creating FHIR-based data structures for learning and prototyping purposes. The setup in this project allows a user to prototype their data needs while also getting IDE support for auto completion and validation without the need to setup a full IG project do accomplish the same goals.

The structures created with this setup can either be proper FHIR Resource instances (based on the official FHIR schemas) or other arbitrary structures used by those Resource instances (i.e. data types, backbone elements, etc.). 

For now, this project is only configured for use with [Visual Studio Code (VSC)](https://code.visualstudio.com/).

This project is still WIP and is likely to be buggy at times until it's been tested by end users. Please add issues to the GitHub repository if you notice any problems or have enhancement ideas.

## Getting started

* Install Visual Studio Code and add the YAML and XML extensions from Red Hat.

* Use File -> Open Workspace... to open the `fhir-examples.code-workspace` workspace file.

* Files created under a `*-resources` directory are treated as FHIR resource files. The content of these files will be validated as proper FHIR **Resource** instances that can be used as is to submit to the appropriate FHIR endpoint.

  * `.json` or `.yaml` files are based on the [JSON resource schema](#json-resource-schema) described below.

  * `.xml` files are based on the [XML resource schema](#xml-resource-schema) described below.

  * There might be limits for what is possible per FHIR version (which is indicated in the directory prefix) See the schema sections for additional information.

* Files created under a `*-examples` directory will allow you to create either a full FHIR **Resource** example, or an example of any FHIR data structure. However, the overall file structure follows an **Example** based template (for the JSON/Yaml format at the moment) with the possibility of multiple examples per file. See the schema section below for additional information.

  * A **FHIR data structure** means creating an example of a data type, a nested complex type (i.e. a backbone element), etc. on its own without needing a full **Resource** instance, or a full **Resource**.

  * `.json` or `.yaml` files are based on the [JSON example schema](#json-example-schema) described below.

  * `.xml` files are based on the [JSON example schema](#xml-example-schema) described below.

* Files named with a `temp-` or `tmp-` prefix will not be committed to Git.

* Folders are prefixed with a FHIR version.

* A file's suffix should be either `.json`, `.yaml` or `.xml` based on the desired format.

* Open your example file in the VSC editor to add your content. VSC should provide autocompletion and validation.

* Auto-completion is triggered with Ctrl+Space and the suggestions will be the valid list of values based on the context. You can start typing while the list is open and this should provide filtering to help find a specific entry.
  
  * Validation errors will be highlighted with colored underlines. You might also notice additional underline highlighting even if your example is valid but this additional highlighting is likely spelling related.
  
  * You can also open and configure the **Problems** view from the View -> Problems menu.

  * Keep in mind that the XML format is order sensitive. The errors and auto completion suggestions are based on the order of elements and the position where the auto completion is triggered.

* See the various **demo** files in the directories. Files can be added to the base `*-resources` and `*-examples` directories, or be grouped in one sub-directory under those base directories. Further directory nesting is not supported.  

## Issues

* See the schema descriptions below to understand some additional differences between what you are able to create within each format. This is still a work in progress and will likely change over time.

* Some support for FSH files in VSC might be possible however I am not yet aware of "schema" level support for FSH files. VSC has "language" support for FSH but I am not aware of any "schema" based validation of FSH files. If you are aware of any schema support for FSH files, please open an issue to describe what I need to implement in this project to facilitate such functionality.

* XSD/XML schemas for 4.6.0+ are currently broken. See: https://chat.fhir.org/#narrow/stream/179166-implementers/topic/xsd.20not.20valid

* One or more of the IDE settings are related to memory and other IDE resource settings. The defaults do not handle the size of the schema files so I had to increase them to a much larger value. Hopefully these high settings won't be an issue on you machines. See the specific settings in the `fhir-examples.code-workspace` workspace file.

# Schemas

The JSON schemas described below support the `.json` and `.yaml` files.  The XML schemas (XSD) are for `.xml` files. The schema files are organized under the `schemas` directory, by version and format.

### JSON resource schemas

* The **resource.json** schemas support creating FHIR Resource instances in JSON or Yaml formats. They contain few fixes compared to the original files. The JSON example schema described below has similar fixes.
    
    * Added missing {"type": "object", ...} keys where needed
    
    * Changed "definitions" to "$defs" and all "$ref" have been updated

### XML resource schema

* This is the actual FHIR XSD/XML schema without changes.

* It supports FHIR Resource examples, one per file. 

* For now there is no XML support for FHIR Versions other than 4.0.1. This will be added when the FHIR XSD schema is fixed. See issues above.

### JSON example schema

* The **example.json** schemas support creating arbitrary FHIR structures in JSON or Yaml formats.

* JSON or Yaml files have the following **Example** template.

    * A file has an object with arbitrary key names. Each key holds an **Example** wrapper object

    * An **example** wrapper object has the following structure. Double quotes are only needed for the JSON format.

        * A `"Title":` key that holds a string as the title of the example. This field is required.

        * A `"Description":` key that holds an array of strings. Each string in the array can represent a sentence, paragraph, etc.  The array helps break up a lengthy text block into multiple parts. Consider this array as the documentation of the example, the use case, etc.

        * A `"Links":` array of objects that contain `"title":` and `"link":` keys. This array helps with holding links to a GitHub issue, references for the example, etc.  The `"title":` key holds some label or name for the link.

        * A `"Schema":` key. This is an enumeration of the various structure schema names for which you can create an example. For example, if you would like to create an example of the CodeableConcept data type, you would use Ctrl+Space to get the suggestions and then type to filter to CodeableConcept.

        * An `"Instance":` key that holds the example. It is an instance of the schema name you selected for the `"Schema":` key.

* This schema works for versions 4.0.1 and 4.6.0. It is applied to `.json` and `.yaml` files under a `*-examples` directory.


### XML structure schema

* This XSD/XML schema supports creating arbitrary FHIR XML structures as described above. It's only available for version 4.0.1.

* It does not yet have the **Example** wrapping structure as described above but this feature will be implemented soon.

* It supports only one structure instance per file.

* It only works for version 4.0.1 and it is applied to `.xml` files under the `4.0.1-structures` directory.

