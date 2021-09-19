# Aluno
* 236773: Igor Gabriel Cavalcante de Carvalho Borges

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH c=(m:Marcador)-[r:Pertence]->(n:Categoria {id:"Serviços"})
RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH c=(m:Categoria)-[r:Superior*]->(n:Categoria {id:"Serviços"})
MATCH d=(o:Marcador)-[s:Pertence]->(p:Categoria)
WHERE p IN nodes(c)
RETURN o
~~~
