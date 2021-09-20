# fuseki-docker-config
docker-compose and some config files for Jena Fuseki

Included:  
Simple [graph](data/graph.ttl):  

```turtle
foaf:agent a owl:Class ;
  rdfs:label "Агент"@ru .

org:Organisation rdfs:subClassOf foaf:Agent ;
  rdfs:label "Организация"@ru .

org:OrganizationalUnit rdfs:subClassOf foaf:Agent ;
  rdfs:label "Организационное подразделение"@ru .

org:Post a owl:Class ;
  rdfs:label 'Должность'@ru .

org:postIn a owl:ObjectProperty ;
    rdfs:domain org:Post ;
    rdfs:range org:OrganizationalUnit .
    rdfs:label "Является должностью подразделения"@RU ;

org:unitOf a owl:ObjectProperty ;
    rdfs:domain org:OrganizationalUnit> ;
    rdfs:range org:Organization ;
    rdfs:label "Является подразделением организации"@RU .
```

And simple [rules](data/rules.ttl):
```turtle
[transit_sc:  (?x rdfs:subClassOf ?y), (?a rdfs:subClassOf ?x) -> (?a rdfs:subClassOf ?y)]
[transit_type:  (?x rdfs:subClassOf ?y), (?a rdf:type ?x) -> (?a rdf:type ?y)]
[transit_p_range:  (?p rdfs:range ?c), (?sc rdfs:subClassOf ?c) -> (?p rdfs:range ?sc)]
[transit_p_domain:  (?p rdfs:domain ?c), (?sc rdfs:subClassOf ?c) -> (?p rdfs:domain ?sc)]
```

