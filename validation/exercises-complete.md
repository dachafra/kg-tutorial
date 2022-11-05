# Exercise 5.1

[SHACL](https://www.w3.org/TR/shacl/) Shapes Constraint Language is 
a language for validating RDF graphs against a set of conditions.
These conditions are provided as shapes, which as also an RDF graph.

Starting from the below SHACL shape, add property shapes for the following predicates
- `foaf:family_name` (required)
- `foaf:givenName` (required)
- `foaf:img` (required)
- `foaf:mbox` (required)
- `foaf:nick` (optional)
- `foaf:homepage` (optional)

Thus, you ignore organizations for now.
Use your solution of exercise 1.1 as input data for the validation.

Tip: try out your SHACL shapes via <https://shacl.org/playground/> 
or <https://shacl-playground.zazuko.com/>.

```turtle
@prefix rdf:   <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs:  <http://www.w3.org/2000/01/rdf-schema#> .
@prefix sh:    <http://www.w3.org/ns/shacl#> .
@prefix foaf:  <http://xmlns.com/foaf/0.1/> .
@prefix ex:    <http://example.com/> .

ex:PersonShape
    a              sh:NodeShape ;
    sh:targetClass foaf:Person ;
    sh:property    ex:requiredGivenName .

ex:requiredGivenName
    a           sh:PropertyShape ;
    rdfs:label  "given name"@en ;
    sh:path     foaf:givenName ;
    sh:nodeKind sh:Literal ;
    sh:minCount 1 .
```

# Exercise 5.2

Starting from your solution for exercise 5.1, add a node shape for organizations. Add property shapes for the following predicates
- `foaf:name` (required)
- `foaf:homepage` (required)
- `foaf:member` (required)


# Exercise 5.3

Starting from your solution for exercise 5.2, make sure that 

- every person belongs to at least one organization.
- there is a sequence path from organization to member and that members have homepage.
- the term types (nodeKind) and datatypes of all properties and values.
- email pattern
- image is actually an image (check the extension)
- nick length is between 3 and 15


# Exercise 5.4

Parse your solution of exercise 5.3 in Python using the library [pySHACL](https://github.com/zazuko/rdf-validate-shacl) and

- Run your shapes against your solution of exercise 1.3 and print results.
- Run your shapes against manual changes to your solution of exercise 1.3 to see if errors are caught and printed.

Tip: Use the Python notebook provided or the Google colab link from the slides
