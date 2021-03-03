# Neo4J Banco de dados a base de grafos

# Introdução - Neo4J

## Neo4J é um banco NOSQL (Not Only SQL), no qual não se utiliza a linguagem de consultas **SQL**(Standard Query Language) pois o banco tem  sua base de dados orientada a grafos e utiliza a linguagem Cypher. Os dados são todos armazenados em formas de *Node*(Nós), podendo conter atributos e relacionamentos com outros nós.

# Estrutura de Armazenamento

### CREATE (: Pessoa{nome:'Allan', usuario:'allan123'}), (:Pessoa{nome:'Teste', usuario:'teste'})

### CREATE (: Artista{nome:'Nirvana', genero:'rock'}), (: Artista{nome:'Soundgarden'})

### CREATE (: Musica{nome:"Where did you sleep last night"})

### MATCH (p1: Pessoa{nome:"Allan"}), (p2: Pessoa{nome:"Teste"}) 
### CREATE (p2)-[:SEGUE]->(p1)

### MATCH (m:Musica{nome:'Where did you sleep last night'}), (a:Artista{nome:'Nirvana'}) 
### CREATE (m)-[:PERTENCE]->(a)

### MATCH (p:Pessoa{nome:'Allan'}), (m:Musica{nome:'Where did you sleep last night'})
### CREATE (p)-[:OUVIU]->(m)

### MATCH (p:Pessoa{nome:'Teste'}), (a:Artista{nome:'Nirvana'})
### CREATE (p)-[:SEGUE]->(a)

### CREATE (: Musica{nome:"Black hole sun", genero:'rock'})

### MATCH (m: Musica{nome:"Black hole sun"}), (a:Artista{nome:'Soundgarden'})
### CREATE (m)-[:PERTENCE]->(a)

### MATCH (p:Pessoa{nome:'Allan'}), (a:Artista{nome:'Soundgarden'})
### CREATE (p)-[:SEGUE]->(a)

### MATCH (p:Pessoa{nome:'Teste'})
### SET p.nome = 'Guilherme'

### MATCH (p:Pessoa{nome:'Guilherme'}) 
### SET p+= {idade:19}

### MATCH (p:Pessoa{nome:'Guilherme'}) 
### SET p.idade = null

### MATCH (p:Pessoa{nome:'Allan'})-[a:OUVIU]->() 
### DELETE a

### MATCH (p:Pessoa{nome:'Guilherme'}) 
### DETACH DELETE p

### MATCH (p:Pessoa{nome:'Allan'}) DELETE p

### MATCH (p:Pessoa{nome:'Allan'}) DETACH DELETE p

### CREATE CONSTRAINT uk_cpf ON (n: Pessoa) ASSERT n.cpf IS UNIQUE



