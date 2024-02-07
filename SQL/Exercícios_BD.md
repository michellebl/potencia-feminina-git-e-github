### Criar a tabela "alunos": 

CREATE TABLE alunos (
    id SERIAL PRIMARY KEY,
    nome TEXT,
    idade INTEGER,
    curso TEXT
);

### Inserir registros na tabela "alunos":

INSERT INTO alunos (nome, idade, curso) VALUES
('João', 25, 'Engenharia'),
('Maria', 22, 'Medicina'),
('Pedro', 19, 'Administração'),
('Ana', 21, 'Engenharia'),
('Carlos', 24, 'Medicina');

Consultas Básicas:
a) Selecionar todos os registros da tabela "alunos":
SELECT * FROM alunos;

b) Selecionar o nome e a idade dos alunos com mais de 20 anos:
SELECT nome, idade FROM alunos WHERE idade > 20;

c) Selecionar os alunos do curso de "Engenharia" em ordem alfabética:
SELECT * FROM alunos WHERE curso = 'Engenharia' ORDER BY nome;

d) Contar o número total de alunos na tabela:
SELECT COUNT(*) AS total_alunos FROM alunos;

### Atualização e Remoção:
a) Atualize a idade de um aluno específico na tabela:
UPDATE alunos SET idade = 23 WHERE nome = 'João';

b) Remova um aluno pelo seu ID:
DELETE FROM alunos WHERE id = 2;

### Criar uma Tabela e Inserir Dados:
CREATE TABLE clientes (
    id SERIAL PRIMARY KEY,
    nome TEXT,
    idade INTEGER,
    saldo FLOAT
);

INSERT INTO clientes (nome, idade, saldo) VALUES
('Cliente A', 35, 1500.50),
('Cliente B', 40, 2000.75),
('Cliente C', 28, 800.25),
('Cliente D', 50, 3000.00);

### Consultas e Funções Agregadas:
a) Selecione o nome e a idade dos clientes com idade superior a 30 anos:
SELECT nome, idade FROM clientes WHERE idade > 30;

b) Calcule o saldo médio dos clientes:
SELECT AVG(saldo) AS saldo_medio FROM clientes;

c) Encontre o cliente com o saldo máximo:
SELECT * FROM clientes WHERE saldo = (SELECT MAX(saldo) FROM clientes);

d) Conte quantos clientes têm saldo acima de 1000:
SELECT COUNT(*) AS clientes_acima_de_1000 FROM clientes WHERE saldo > 1000;

### Atualização e Remoção com Condições:
a) Atualize o saldo de um cliente específico:
UPDATE clientes SET saldo = 2500 WHERE nome = 'Cliente A';

b) Remova um cliente pelo seu ID:
DELETE FROM clientes WHERE id = 3;

### Junção de Tabelas:
CREATE TABLE compras (
    id SERIAL PRIMARY KEY,
    cliente_id INTEGER REFERENCES clientes(id),
    produto TEXT,
    valor REAL
);

INSERT INTO compras (cliente_id, produto, valor) VALUES
(1, 'Produto X', 100.50),
(2, 'Produto Y', 200.75),
(1, 'Produto Z', 50.25),
(4, 'Produto X', 300.00);

SELECT clientes.nome, compras.produto, compras.valor
FROM clientes
JOIN compras ON clientes.id = compras.cliente_id;

