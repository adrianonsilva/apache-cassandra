# Cassandra

- [1. Descrição](#link1)
- [2. Instalação](#link2)
- [3. Comandos básicos](#link3)
- [4. Links](#link4)

<a id="link1"></a>
## 1. Descrição

O Apache Cassandra é um banco de dados NoSQL colunar que permite operações de leitura e gravação em grandes datasets.

Na sua arquitetura todos os nós são iguais, mão possuindo um "master", dessa forma não possuindo um ponto de falha.

Outra diferencial, é a Cassandra Query Language (CQL), que permite a manipulação de objetos (create, drop ...) e dados (insert, update ...)

<a id="link2"></a>
## 2. Instalação

#java</br>
![Screenshot](/images/c01.jpg)

#python</br>
![Screenshot](/images/c02.jpg)

#download</br>
```wget https://downloads.apache.org/cassandra/3.11.9/apache-cassandra-3.11.9-bin.tar.gz```

#extract
```tar xvzf apache-cassandra-3.11.9-bin.tar.gz```

#mover para a pasta destino e permissões para o usuário padrão</br>
```sudo mv apache-cassandra-3.11.9 /usr/local/cassandra```</br>
```sudo chown -R hduser /usr/local/cassandra```</br>

![Screenshot](/images/c03.jpg)

## Configuração

#editar bashrc</br>
```nano ~/.bashrc```</br>
```export CASSANDRA_HOME=/usr/local/cassandra```</br>
```export PATH=$PATH:$CASSANDRA_HOME/bin```</br>
```export CLASSPATH=$CLASSPATH:/usr/local/cassandra/lib/*```</br>
```source ~/.bashrc```</br>

![Screenshot](/images/c04.jpg)

#criar diretórios</br>

```mkdir /usr/local/cassandra/data```</br>
```mkdir /usr/local/cassandra/commitlog```</br>
```mkdir /usr/local/cassandra/saved_caches```</br>

![Screenshot](/images/c05.jpg)

#editar cassandra.yaml</br>
```nano /usr/local/cassandra/conf/cassandra.yaml```</br>

```data_file_directories:```</br>
```    - /usr/local/cassandra/data```</br>

```commitlog_directory: /usr/local/cassandra/commitlog```</br>
```saved_caches_directory: /usr/local/cassandra/saved_caches```</br>

![Screenshot](/images/c06.jpg)

![Screenshot](/images/c07.jpg)

#start cassandra</br>
```cassandra```</br>

![Screenshot](/images/c08.jpg)

![Screenshot](/images/c09.jpg)

#conferência dos diretórios</br>

![Screenshot](/images/c10.jpg)

#conferindo a instalação</br>

![Screenshot](/images/c10a.jpg)

#iniciando a interface (CQL)</br>

![Screenshot](/images/c11.jpg)

#select em uma tabela</br>

![Screenshot](/images/c12.jpg)

<a id="link3"></a>
## 3. Comandos básicos

#criando um Keyspace

Um Keyspace é um namespace que define a replicação de dados entre os nodes.</br>
Em um cluster existe um Keyspace por node.</br>

```CREATE KEYSPACE teste WITH REPLICATION = { 'class' : 'NetworkTopologyStrategy', 'datacenter1' : 3 } AND DURABLE_WRITES = false;```</br>

![Screenshot](/images/c13.jpg)

![Screenshot](/images/c14.jpg)

#criando uma tabela</br>

```CREATE TABLE emp(emp_id int PRIMARY KEY,emp_name text,emp_city text,emp_sal varint,emp_phone varint);```

![Screenshot](/images/c15.jpg)

#inserindo dados</br>

```INSERT INTO emp (emp_id, emp_name, emp_city,emp_phone, emp_sal) VALUES(1,'ram', 'Hyderabad', 9848022338, 50000);```</br>
```INSERT INTO emp (emp_id, emp_name, emp_city,emp_phone, emp_sal) VALUES(2,'robin', 'Hyderabad', 9848022339, 40000);```</br>
```INSERT INTO emp (emp_id, emp_name, emp_city,emp_phone, emp_sal) VALUES(3,'rahman', 'Chennai', 9848022330, 45000);```</br>

![Screenshot](/images/c16.jpg)

<a id="link4"></a>
## 4. Links

Apache Cassandra</br>
https://cassandra.apache.org/</br>

Bancos Colunar</br>
https://en.wikipedia.org/wiki/Column-oriented_DBMS</br>



