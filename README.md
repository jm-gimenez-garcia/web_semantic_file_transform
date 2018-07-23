# SPARQL dataset transformer:
This code will transform SPARQL queries from RDF reification, N-ary relations, Singleton property, Ndfluents to Named Graphs.
#### Example:
This dataset is in RDF reification:
```
PREFIX rdf:  <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
SELECT * WHERE{
    ?st rdf:type rdf:statement.
    ?st rdf:subject ?s.
    ?st rdf:predicate ?p.
    ?st rdf:object ?o.
}
```
When converted into a named graph dataset the result will be :
```
SELECT * WHERE{GRAPH ?st {?s ?p ?o .}}
```


#### Requirements:
1. JDK 1.8
2. Maven

First run this command on the project path to build the jar file:
```
$ mvn clean package
````

To execute the generated jar file:
```
$ java -jar target\SparqlTransform-1.0-SNAPSHOT-jar-with-dependencies.jar -t "query_type" -d "dataset_path" -q "SPARQL_query" -m "query_mapping" 
```
- **-q** : will take SPARQL dataset as an argument.
- **-t** : will take the SPARQL dataset type(reification,singleton,ndfluents,nary).
- **-d** : will take the path of the dataset that we want to dataset.
- **-m** : will take the metadata of the dataset we use it in ndfluents and n-ary relations.

You can check the web version [here](http://wdaqua-dataset-transformation.univ-st-etienne.fr/).
