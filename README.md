# Also see [this README](examples/README.md)

# Introduction

The goal of this project is to support creating FHIR-based data structures for learning and prototyping purposes. The setup in this project allows a user to prototype their data needs while also getting IDE support for auto completion and validation. This approach is a bottom up approach where use cases are demonstrated by examples without the need to setup a full IG project to accomplish the same goals.

The examples created with this setup can either be proper FHIR Resource instances (based on the official FHIR schemas) or other arbitrary FHIR structures used by those Resource instances (i.e. data types, backbone elements, etc.). 

For now, this project is only configured for use with [Visual Studio Code (VSC)](https://code.visualstudio.com/).

This project is still WIP and is likely to be buggy at times until it's been tested by end users. Please create issues at [the GitHub repository](https://github.com/ShahimEssaid/fhirware.fhir-examples) if you notice any problems or have enhancement ideas.

# Getting started

* Install Visual Studio Code and add the YAML extension from Red Hat.

* Use File -> Open Workspace... to open the `fhir-examples.code-workspace` workspace file.

