# Bases de Datos Orientada a Grafos
Aquí aprenderás los principios basicos de las bases de datos orientadas a Grafos y la comparación entre éstas y las bases de datos tipo relacionales. 

## ¿Qué es un grafo?
Un grafo es un tipo de estuctura de datos que consiste en un conjunto de nodos(vértices) conectados mediante relaciones(aristas o arcos).  
En cuanto a las Bases de Datos orientadas a Grafos se basan en éstas representaciones en donde cada nodo corresponde a una identitad que contiene ciertas propiedades y la forma en la que se conectan entre ellas, de tal forma que pertime establecer una cantidad inmensa de diferentes tipos de relaciones.



**Algunas de las Bases de Datos Orientadas a Grafos más conocidas**
- Neo4j
- Amazon Neptun
- SAP Hana Graph
- OrientDB
- ArangoDB

## Neo4j
Neo4j utiliza el lenguaje Cypher, un lenguaje muy sencillo de entender. Este se basa en las etiquetas, las etiquetas podrían ser relacionadas como a las cabeceras de las tradicionales tablas en una base de Datos como MySql.
La ventaja que tiene el lenguaje Cypher es que no necesitamos declarar tantos ` JOIN` para establecer relaciones complejas.

Comienza con Neo4j [aquí](https://neo4j.com/)

### Comandos Básicos con Cypher
Estos son algunos de los moldes para las operaciones básicas de un CRUD

- CREAR
    1. Crear nodos

        ` CREATE (Miriam:Person { name: "Miriam"}), (Rosa:Person { name: "Rosa"}) `
    2. Crear relaciones

        ` MATCH (Miriam:Person { name: "Miriam"}), (Rosa:Person { name: "Rosa"}) CREATE (Miriam)-[:FRIENDS_WITH]->(Rosa) `

- ELIMINAR
    1. Eliminar nodo

        ` MATCH (Miriam:Person {name: "Miriam"}) DELETE Miriam`

    ***Nota*** *:Solo se puede eliminar un nodo de esta forma cuando no tiene una relación que lo conecte a otro nodo; dado este caso se tendrá que eliminar la relación que los une para depués eliminar los nodos.*

    2. Eliminar relación

        ` MATCH (n { name: "Miriam"})-[r:FRIENDS_WITH]->(p { name: "Rosa"}) DELETE r `

    3. Eliminar todo el grafo

        ` MATCH (n) OPTIONAL MATCH (n)-[r]-() DELETE n, r `

- BÚSQUEDA
    1. Por relaciones y propiedades

        ` MATCH (n:Person)-[k:KNOWS]->(f) WHERE k.since < 2000 RETURN f.name, f.age, f.email `

        ` MATCH (n:Person) WHERE (n)-[:KNOWS]-({ name: 'Timothy' }) RETURN n.name, n.age `

- ACTUALIZAR
    1. Añadir propiedad

        ` MATCH (n { name: “Andy” }) SET n.surname = “Taylor” RETURN n.name, n.surname `

    2. Eliminar propiedad

        `MATCH (a { name: "Andy" }) REMOVE a.age RETURN a.name, a.age`

        ` MATCH (a { name: "Andy" }) SET a = { } RETURN a.name, a.age`


Puedes encontrar muchos más comandos en la [Documentación](https://neo4j.com/docs/cypher-manual/current/) del lenguaje Cypher.

## Conclusión
Al final podemos entender a las Bases de Datos Orientado a Grafos es una alternativa a las bases de Datos relacionales, es sin duda un nuevo modelo que ha sabido ganar popularidad en el mundo tecnológico, en especial entre los analístas de datos. Aún así, la elección sobre que modelo utilizar debería ser basada en la forma más conveniente para el problema que se presenta, es decir de qué forma es más fácil representar los datos para su comprensión, por lo tanto, no hay mejor estructura o peor, solo hay mejores adaptados a cierto problema.

#### Para más información 
 - Robinson, I., Webber, J. & Eifrem, E. (2015). Graph Databases: New Opportunities for Connected Data. (2da ed.) : O’Reilly Media
 - [Diapositivas](https://drive.google.com/file/d/1ffjU8l3w3FlM7r_0DgLhX8thkDKkbk3A/view?usp=sharing)
 - Puede consultar el [resumen](https://youtu.be/KlGdhf9rgRM) de la clase aquí.