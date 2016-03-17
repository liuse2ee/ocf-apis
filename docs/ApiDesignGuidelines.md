# Api Design Guidelines.
This file defines conventions to foster consistency across the API's proposed by the different TG's and ease the navigation through the OCF API. 

## File name suffix convention and directory structure.

    /—|*.raml
      |— examples/*-example.json
      |— schemas/*-schema.json
      |— traits/*.raml
      |— etc..

## RAML file
### File name selection. 
The resources supported by a specific server are exposed through the content of the /oic/res resource.

To interact with a specific resource, a client needs to discover 2 additional details: The location of the resource and the API supported by the resource.
- The location of the supported resources can dynamically be discovered through the /oic/res resource.
- The api (supported methods, payload format, …) of the supported resources can also be dynamically discovered from the /oic/res resource using the associated rt value. 

This information on its own doesn't provide sufficient dynamic information to extract the api unless we have a convention in place to associate the rt value with the location where the api (the raml formatted api definition) details can be extracted.
For this reason, the proposal for naming the raml files is to use the rt value as prifix and the .raml as suffix.

### Example:
A resource defined in the /oic/res with an "rt" value of "oic.wk.p" would have it's api definition in a raml file named:

    oic.wk.p.raml

## JSON schemas

### 'id' selection for schema
In order the avoid clashes between schema definitions and allow for reltive schema referencing, there is a need for defining the namespace in which each TG can freely work.

### 'id' naming convention:
All schema id's should have the .json suffix.
The base url of a schema id should be composed of:
* ocf domain: https://www.openconnectivity.org/
* the path: ocf-apis/\[submodule name\]/schemas/
* name: \*-schema.json

### Example
example for oic.wk.p 
    
    "id": "https://www.openconnectivity.org/ocf-apis/core/schemas/oic.wk.p-schema.json#"
