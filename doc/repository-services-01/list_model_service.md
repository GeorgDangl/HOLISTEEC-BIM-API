# HOLISTEEC List Models Service #

* [Level Up](../README.md)
* [Overview](./README.md)

**Retrieve a collection of model descriptions where the currently logged on user has read access.**

## List Model Parameters

**TODO: filtering using meta data**


I/O/opt	| Parameter | Type | Comment |
--------|-----------|------|---------|
In  	|model_meta_data	|[model_meta_data](schemas/model_meta_data.md)	| Model meta data for filtering, see below for mandatory fields
-|-|-|-|-				
Out 	|Model URL 			|String			|URL to the model data on the target server 
Out 	|Model Meta Data 	|[model_meta_data](schemas/model_meta_data.md)	|Full model meta data as stored on the server.

The following model meta data fields are mandatory:

* repository_name :States which server repository to use. If not given, the default repository will be used. If the repository does not exist, an error will be raised.


##REST/JSON interface

repository_name is given in the resource URL

Element | Content|
--------|--------|
**Resource URL** 	|*GET /hol-repos/{version}/{repository_name}/models*
*hol-repos*			|Shorthand for HOLISTEEC Repository Services
*version*			|States version of the API to use, allowing multiple versions of API for upgrading.
*repository_name*	|States which server repository to use. If not given, the default repository will be used. If the repository does not exist, an error will be raised.

JSON Schema not available (trivial)

##REST/JSON Example

This example shows two versions of one model and one version of another
```

GET https://bim--it.net/bcf/Repository/1.0/HOL-repos/Models

Request:
	n.a

Response:
[{
    "model_url ": "https://bim--it.net/bcf/Repository/1.0/HOL-repos/Models/BFCA32BA48BEEE444111AB",
    "model_meta_data ":
    {
        "model_guid ": "BFCA32BA48BEEE444111AB",
	    "repository_name ": "HOL-repos",
	    "model_name ": "Barra_Architecture",
	    "model_type ": "IFC4",
	    "model_version ": "V1",
	    "description ": "Alternative 1 for Architecture",
	    "domain_name": "Architecture",
    }
},
{
    "model_url ": "https://bim--it.net/bcf/Repository/1.0/HOL-repos/Models/ABC113BB59BE23444F1FAF",
    "model_meta_data ":
    {
        "model_guid ": "ABC113BB59BE23444F1FAF",
	    "repository_name ": "HOL-repos",
	    "model_name ": "Barra_Architecture",
	    "model_type ": "IFC4",
	    "model_version ": "V2",
	    "description ": "Alternative 2 for Architecture",
	    "domain_name": "Architecture",
    }
},
{
    "model_url ": "https://bim--it.net/bcf/Repository/1.0/HOL-repos/Models/BA1E44AA11BCBB455122AB",
    "model_meta_data ":
    {
        "model_guid ": "BA1E44AA11BCBB455122AB",
	    "repository_name ": "HOL-repos",
	    "model_name ": "Barra_HVAC",
	    "model_type ": "IFC4",
	    "model_version ": "V1",
	    "description ": "Alternative 1 for the HVAC",
	    "domain_name": "HVAC",
    }
}]
```
