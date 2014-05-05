RDF Constraint Language
------------------------------------------

As with any generic meta-model there comes a need to be able to describe the shape of data for use in introspection and for constraint validation. For example XML has XMLSchema[1] and RelaxNG. While the RDF stack has existing parts that begin to address the need for a data model description language and constraint language, such as OWL[5] and RDFS[6] they are either underpowered or bring with them unwanted semantics. The RDF Constraint Langauge (RDFCL) describes a vocabulary for describing RDF data models and validation semantics for checking the correctness of a given graph in respect to a given data model and a give set of constraints.

Introduction
------------

When working with data systems and users want to know several things, they want to have an explicit description of the shape of the data, and they would like to know if a given set of data is valid with respect to the description of a data model. In XML, XMLSchema acts as a description of the shape of the data and along with the validation semantics can be used to check if a given document is valid in respect to a given schema. 

[fix when finished]
This specification is split into several sections, the first section introduces the overall approach and key concepts. The second section presents the RDF vocabulary used for describing a RDF Schema and the thrid section describes the validation semantics. The paper concludes with a discussion of possible future directions.

Data Modelling and Validation Core Concepts
-------------------------------------------

Data Modelling and validation can be seen as two sides of the same thing. A data structure description is concerned with unambiguously defining the shape of a data model. For example, to communicate that in a given model there can exist things of type 'person' and that instances of this type must have a property called 'birthdate' whose value is of type datetime. The description is itself a data model that can be viewed, queried and manipulated. A typical use case for this is to create user interfaces for items of a given type. 

A data structure description can also be considered as a set of constraints. Validation of a given RDF graph is about executing the set of validation rules associated with the different constraint types being used. Each constraint type has a well defined validation rule. This rule is expressed as a parameterised SPARQL query. The parameters are provided by the instance of the constraint being validated. 

In RDFCL a set of constraints is called a schema. To validate a schema all the constraints in the schema must be valid. 

There are two general classes of constraint. Core constraints are basic constraints that are simple to evaluate and are generally concerned with constraining the nature of instances. E.g. to say that all instances of type person must have exactly one birthdate property.

The other class of constraints are extension constraints. These constraints consist of a SPARQL query. This class of constraints support arbitrarily complex constraint rules that can apply more widely.

As well as constraints, RDFCL also defines a set of global validation rules. These rules are defined as SPARQL queries that check the validity of an entire graph.


RDFCL Data Model and Constraint Validation Rules
-------------------------------------------------

RDFCL is defined in terms of a number of constraint types and declarations. For each constraint type the required and optional properties of that type are described. RDFCL declarations are global in scope. This means they are not evaluated against a specific constraint but apply to the entire data model instance. 

As well as the data model description of an constraint type the evaluation rule for the type is also provided. These evaluation rules are defined in terms of a context, the constraint and a SPARQL query. The SPARQL query is used as means to unambiguously express the semantics and does not imply that SPARQL must be used when implementing RDFCL.

Declarations
------------

Declarations are statements in the model that have related global validation rules. The two things are indirectly connected. The following sections describe the set of global validation rules. When validating a schema against a model instance these rules are always tested before the schema constraints. 

RDFCL Class Global Validation Rule
----------------------------------

Making a resource an instance of rdfcl:Class is a declaration that the resource may be used as a type for other resources.  

Example:

example:person rdf:a rdfcl:Class

The global validation rule associated with this declaration is describes as follows:

No instance may have a type where that type is not declared to be an instance of rdfcl:Class.

Formally:
This constraint is violated when:

select count(?instance) where { ?instance a ?type . ?type a ?class. ?class not rdfcl:Class } > 0       

RDFCL Property Class Global Validation Rule
---





Schema Entity
-------------

A schema is a grouping element for a set of constraints.  



Validation Semantics
--------------------



       



























 
   