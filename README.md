RDF Constraint Language (RDFCL)
=====

The RDF Constraint Langauge RDFCL defines a collection of constraint types that can be used to describe and validate RDF model instances. RDFCL contains a number of built in constraint type and also provides an extension mechanism that allows for the execution of arbitrary SPARQL expressions. 

Each constraint type is defined in terms of an RDF data structure and related evaluation semantic. An RDF graph is valid with respect to constraint if the evaluattion of the constraint validation for that constraint instance is valid.

A schema is defined to comprise a set of instances of RDFCL constraints. An RDF model is valid with respect to a schema if all the constraints comprising the schema are valid. Constraints can be evaluated in any order and do not affect one another.

Motivation
====

Many people coming to RDF think in terms of UML-esque data modelling whereas the majority of those creating RDF are coming from the logic and AI communities. Not much work has been done to make it easier for the entity, class type centric people to quickly create the things they want in RDF. 

Also, existing approaches to constraints and validation are either under powered, overly complex and/ or bring with them unwanted entailment semantics. 

RDFCL is an attempt to create something simple and powerful that java and c# developers, for example, can more easily relate to and use.

Also, the simplicity and smallness of constraint types allow people to quickly implement the validation semantics in an existing RDF platform. 


Related Work
====

To further encourage adoption of this constraint language the RDF Modelling and Instance Language has been developed. This is a syntax that when processed produces RDF. The unique thing about this syntax is that is is optimised for expressing schemas defined using RDFCL. RMIL can be found at http://github.com/SesamResearch/rmil






