```sql
-- Criando as tabelas
DROP TABLE IF EXISTS company.funcionarios;
CREATE TABLE company.funcionarios(
			id INT AUTO_INCREMENT PRIMARY KEY,
			nome VARCHAR(50), 
			manager_id INTEGER 
);

DROP TABLE IF EXISTS company.gerentes;
CREATE TABLE company.gerentes(
					id INTEGER, 
					nome VARCHAR(50), 
					equipe VARCHAR(50) 
);

INSERT INTO company.funcionarios (nome, manager_id) VALUES
          ('Ana', 1001), 
          ('Carlos', 2002), 
          ('Beatriz', 3003), 
          ('Fernando', 4004), 
          ('Juliana', 1001), 
          ('Rafael', 1001), 
          ('Mariana', 2002), 
          ('Lucas', 3003), 
          ('Sofia', 4004), 
          ('Gustavo', 1001), 
          ('Camila', 1001), 
          ('Eduardo', 2002), 
          ('Letícia', 3003), 
          ('Rodrigo', 4004), 
          ('Tatiane', 2002), 
          ('Gabriel', 1001), 
          ('Alice', 1001), 
          ('Felipe', 1001), 
          ('Larissa', 2002), 
          ('Thiago', 3003), 
          ('Natália', 4004), 
          ('André', 1001), 
          ('Paula', 2002), 
          ('Vinícius', 3003), 
          ('Renata', 4004), 
          ('Daniel', 1001), 
          ('Bruna', 1001), 
          ('Guilherme', 2002), 
          ('Amanda', 3003), 
          ('Pedro', 4004);

INSERT INTO company.gerentes (id, nome, equipe) VALUES
			(1001, 'Leonardo', 'Equipe Alpha'),
			(2002, 'Fernanda', 'Equipe Beta'),
			(3003, 'Ricardo', 'Equipe Gama'),
			(4004, 'Patrícia', 'Equipe Delta');
            
-- DESAFIO 1: ​Escreva uma consulta para identificar o gerente com o maior tamanho de equipe. 
-- Você pode assumir que existe apenas um gerente com o maior tamanho de equipe.

SELECT * FROM company.gerentes;

-- Realizando um LEFT JOIN das tabelas
WITH equips AS (

	SELECT func.id, func.manager_id, heads.nome AS gerente_nome, heads.equipe
	FROM company.funcionarios AS func
	LEFT JOIN company.gerentes AS heads
	ON func.manager_id = heads.id
)
SELECT manager_id, gerente_nome, COUNT(*) AS tamanho_equip
FROM equips 
GROUP BY manager_id, gerente_nome
ORDER BY tamanho_equip DESC
LIMIT 1; -- Retorna apenas o gerente com maior equipe

-- DESAFIO 2: Nós temos duas tabelas, uma tabela de cadastro de nossos consumidores com diversas informações, 
-- dentre elas, a cidade nas quais eles moram; e uma contendo diversas cidades onde nossos produtos estão disponíveis. 
-- Primeiro, escreva uma consulta que retorne todas as cidades que têm mais de 5 consumidores dos nossos produtos. 
-- E uma segunda que retorne as cidades e as respectivas idades médias de seus consumidores. Utilize 1 de janeiro 
-- de 2024 como data para o cálculo da idade e retorne a consulta em ordem decrescente.

DROP TABLE IF EXISTS company.consumidores;
CREATE TABLE company.consumidores (
						id INT AUTO_INCREMENT UNIQUE,
						primeiro_nome VARCHAR(50),
						ultimo_nome VARCHAR(50),
						data_nascimento DATETIME,
						telefone INT,
						cidade_id INT,
						data_criacao DATETIME
 );       
 
 DROP TABLE IF EXISTS company.cidades;
 CREATE TABLE company.cidades(
				id INT,
				nome VARCHAR(50),
				estado_id INT
); 

INSERT INTO company.consumidores (primeiro_nome, ultimo_nome, data_nascimento, telefone, cidade_id, data_criacao) VALUES
			('Ana', 'Silva', '2000-05-15 00:00:00', 987654321, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Carlos', 'Ferreira', '1998-11-30 00:00:00', 954321987, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Beatriz', 'Mendes', '2002-02-20 00:00:00', 965437821, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Fernando', 'Costa', '1995-09-10 00:00:00', 987653214, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Juliana', 'Almeida', '2001-08-25 00:00:00', 976548932, 105, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Rafael', 'Pereira', '1999-04-12 00:00:00', 987531245, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Mariana', 'Santos', '2003-06-05 00:00:00', 954328765, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Lucas', 'Rodrigues', '2000-01-01 00:00:00', 943219876, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Sofia', 'Martins', '1997-07-19 00:00:00', 976543218, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Gustavo', 'Oliveira', '1996-12-22 00:00:00', 934567891, 105, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Camila', 'Lima', '2002-03-15 00:00:00', 965432198, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Eduardo', 'Barbosa', '1994-10-08 00:00:00', 976543921, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Letícia', 'Ramos', '2001-11-17 00:00:00', 976549832, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Rodrigo', 'Cardoso', '1998-05-29 00:00:00', 987651234, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Tatiane', 'Monteiro', '1993-09-11 00:00:00', 965478321, 105, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Gabriel', 'Vieira', '2004-04-07 00:00:00', 954321876, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Alice', 'Cunha', '2000-07-14 00:00:00', 987654312, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Felipe', 'Gomes', '1995-02-27 00:00:00', 954328761, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Larissa', 'Araujo', '1999-12-13 00:00:00', 976543987, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Thiago', 'Moreira', '1997-06-21 00:00:00', 965439872, 105, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Natália', 'Reis', '2003-05-30 00:00:00', 987651243, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('André', 'Teixeira', '2001-08-09 00:00:00', 954321872, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Paula', 'Melo', '1996-10-15 00:00:00', 976549873, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Vinícius', 'Souza', '1995-03-22 00:00:00', 954328745, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Renata', 'Andrade', '1998-09-18 00:00:00', 976543921, 105, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Daniel', 'Nogueira', '2000-01-06 00:00:00', 987654329, 101, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Bruna', 'Xavier', '1993-11-28 00:00:00', 965432187, 102, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Guilherme', 'Torres', '2002-12-24 00:00:00', 976543987, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
            ('Fernanda', 'Torres', '1969-10-28 00:00:00', 971033987, 103, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY)),
			('Amanda', 'Fernandes', '1999-07-02 00:00:00', 954321869, 104, DATE_ADD('2023-01-07', INTERVAL FLOOR(RAND() * 180) DAY));
            
INSERT INTO company.cidades (id, nome, estado_id) VALUES
			(101, 'São Paulo', 001),
			(102, 'Rio de Janeiro', 002),
			(103, 'Belo Horizonte', 003),
			(104, 'Santo André', 001),
			(105, 'Porto Alegre', 005);
    
-- Fazendo um join entre as tabelas  
WITH morethan5 AS(
	SELECT cons.id, cons.primeiro_nome, cons.ultimo_nome, cons.data_nascimento, cons.telefone, cons.data_criacao, cities.nome, cities.estado_id	
	FROM company.consumidores AS cons
	LEFT JOIN company.cidades AS cities
	ON cons.cidade_id = cities.id
)
SELECT nome, COUNT(*) AS cidade_p5
FROM morethan5
GROUP BY nome
HAVING COUNT(*) > 5
ORDER BY cidade_p5 DESC;

/* 1. Cria a CTE morethan5, juntando consumidores e cidades. 2. Usa a CTE para contar consumidores por cidade (COUNT(*) AS cidade_p5). 3. Filtra cidades com mais de 5 consumidores (HAVING COUNT(*) > 5). 4. Ordena os resultados do maior para o menor (ORDER BY cidade_p5 DESC).
*/

WITH idade_media AS(
	SELECT cons.id, cons.primeiro_nome, cons.ultimo_nome, cons.data_nascimento, cons.telefone, cons.data_criacao, cities.nome AS cidade, cities.estado_id,
	TIMESTAMPDIFF(YEAR, cons.data_nascimento, "2024-01-01") AS idade
    FROM company.consumidores AS cons
	LEFT JOIN company.cidades AS cities
	ON cons.cidade_id = cities.id
)
SELECT cidade, AVG(idade) AS media_idade
FROM idade_media
GROUP BY cidade
ORDER BY media_idade ASC;

-- DESAFIO 3: Escreva uma query que encontre linhas duplicadas numa tabela chamada pedidos e que contém as colunas 
-- cpf, nome, cidade e numero_pedido.

DROP TABLE IF EXISTS company.pedidos;
CREATE TABLE company.pedidos(
			CPF CHAR(9),
            nome VARCHAR(50),
            cidade VARCHAR(50),
            numero_pedido VARCHAR(50)
);

INSERT INTO company.pedidos (CPF, nome, cidade, numero_pedido) VALUES
			('123456789', 'Ana Silva', 'São Paulo', '384275'),
			('234567890', 'Carlos Ferreira', 'Rio de Janeiro', '927143'),
			('345678901', 'Beatriz Mendes', 'Belo Horizonte', '536821'),
			('456789012', 'Fernando Costa', 'Curitiba', '184652'),
			('567890123', 'Juliana Almeida', 'Porto Alegre', '492761'),
			('678901234', 'Rafael Pereira', 'São Paulo', '725489'),
			('789012345', 'Mariana Santos', 'Rio de Janeiro', '316872'),
			('890123456', 'Lucas Rodrigues', 'Belo Horizonte', '638214'),
			('901234567', 'Sofia Martins', 'Curitiba', '852673'),
			('012345678', 'Gustavo Oliveira', 'Porto Alegre', '294387'),
			('123450987', 'Camila Lima', 'São Paulo', '639471'),
			('234560876', 'Eduardo Barbosa', 'Rio de Janeiro', '748915'),
			('345670765', 'Letícia Ramos', 'Belo Horizonte', '527849'),
			('456780654', 'Rodrigo Cardoso', 'Curitiba', '893412'),
			('567890543', 'Tatiane Monteiro', 'Porto Alegre', '671843'),
			('678900432', 'Gabriel Vieira', 'São Paulo', '452918'),
			('789010321', 'Alice Cunha', 'Rio de Janeiro', '782365'),
			('123459807', 'Natália Reis', 'São Paulo', '938476'),
			('901230109', 'Larissa Araujo', 'Curitiba', '673928'),
			('123459807', 'Natália Reis', 'São Paulo', '512389'),
			('123459807', 'Natália Reis', 'São Paulo', '736428'),
			('234569706', 'André Teixeira', 'Rio de Janeiro', '915482'),
			('345679605', 'Paula Melo', 'Belo Horizonte', '482673'),
			('456789504', 'Vinícius Souza', 'Curitiba', '648723'),
			('567899403', 'Renata Andrade', 'Porto Alegre', '328157'),
			('678909302', 'Daniel Nogueira', 'São Paulo', '478126'),
			('789019201', 'Bruna Xavier', 'Rio de Janeiro', '652493'),
			('890129100', 'Guilherme Torres', 'Belo Horizonte', '839125'),
			('901239999', 'Amanda Fernandes', 'Curitiba', '264837'),
			('890129100', 'Guilherme Torres', 'Belo Horizonte', '382946'),
			('123459777', 'João Batista', 'São Paulo', '492716'),
			('234569666', 'Carolina Ribeiro', 'Rio de Janeiro', '719284'),
			('345679555', 'Samuel Castro', 'Belo Horizonte', '543827'),
			('456789444', 'Tatiana Albuquerque', 'Curitiba', '821734'),
			('567899333', 'Henrique Fonseca', 'Porto Alegre', '391527'),
			('678909222', 'Larissa Rocha', 'São Paulo', '735294'),
			('789019111', 'Matheus Andrade', 'Rio de Janeiro', '847561'),
			('890129000', 'Vanessa Costa', 'Belo Horizonte', '923467'),
			('901239899', 'Ricardo Xavier', 'Curitiba', '546823'),
			('012349788', 'Fernanda Duarte', 'Porto Alegre', '782416');

USE company;  -- apenas para reforçar, pois deu erro.          
WITH pedidos_repetidos AS(
		SELECT numero_pedido, COUNT(numero_pedido) AS qntd_rept 
		FROM company.pedidos 
		GROUP BY numero_pedido
		HAVING qntd_rept > 1
)
SELECT company.p.* 
FROM company.pedidos AS p
JOIN pedidos_repetidos pd
ON p.numero_pedido = pd.numero_pedido;


-- DESAFIO 4: ​Na tabela 'pedidos' do DESAFIO 3, encontre os top 5 maiores compradores.
-- TOP 5 compradores
SELECT CPF, nome, COUNT(*) AS total_pedidos
FROM company.pedidos
GROUP BY CPF, nome
ORDER BY total_pedidos DESC
LIMIT 5;

-- DESAFIO 5: ​Você trabalha em um delivery de comida e precisa obter a receita dos motoqueiros cadastrados na 
-- plataforma. Você possui uma tabela chamada CADASTRO com as informações demográficas dos motoqueiros, uma chamada 
-- PRECO com o valor por quilômetro da corrida de acordo com o bairro e uma chamada VIAGENS com informações das 
-- viagens feitas por cada motoqueiro. Construa uma tabela com os 100 motoqueiros mais bem remunerados da plataforma 
-- no mês de Janeiro de 2024.

DROP TABLE IF EXISTS company.cadastros_delivery;
CREATE TABLE company.cadastros_delivery (
				id INT,
				primeiro_nome VARCHAR(50),
				ultimo_nome VARCHAR(50),
				data_nascimento DATETIME,
				telefone CHAR(9)
);

DROP TABLE IF EXISTS company.preco_delivery;
CREATE TABLE company.preco_delivery(
				id INT,
				nome VARCHAR(50),
				preco FLOAT
);

DROP TABLE IF EXISTS company.viagem_delivery;
CREATE TABLE company.viagem_delivery(
			id_motoqueiro INT,
			percurso_em_km FLOAT,
			data DATETIME,
            id_bairro INT
);




INSERT INTO company.cadastros_delivery (id, primeiro_nome, ultimo_nome, data_nascimento, telefone) VALUES
			(10000, 'Ana', 'Silva', '1990-05-12 10:30:00', '912345678'),
			(10001, 'Carlos', 'Ferreira', '1985-07-20 15:45:00', '923456789'),
			(10002, 'Beatriz', 'Mendes', '1998-02-28 08:15:00', '934567890'),
			(10003, 'Fernando', 'Costa', '1992-11-11 17:25:00', '945678901'),
			(10004, 'Juliana', 'Almeida', '1980-04-05 12:00:00', '956789012'),
			(10005, 'Rafael', 'Pereira', '1993-09-30 14:10:00', '967890123'),
			(10006, 'Mariana', 'Santos', '1997-06-18 09:05:00', '978901234'),
			(10007, 'Lucas', 'Rodrigues', '1989-12-22 18:35:00', '989012345'),
			(10008, 'Sofia', 'Martins', '1995-08-14 13:50:00', '900123456'),
			(10009, 'Gustavo', 'Oliveira', '1984-01-01 07:20:00', '911234567'),
			(10010, 'Camila', 'Lima', '1991-10-07 11:40:00', '912349876'),
			(10011, 'Eduardo', 'Barbosa', '1987-06-19 16:05:00', '923459765'),
			(10012, 'Letícia', 'Ramos', '1994-03-25 09:30:00', '934567654'),
			(10013, 'Rodrigo', 'Cardoso', '1982-08-10 17:45:00', '945678543'),
			(10014, 'Tatiane', 'Monteiro', '1999-12-15 12:20:00', '956789432'),
			(10015, 'Gabriel', 'Vieira', '1986-05-31 14:50:00', '967890321'),
			(10016, 'Alice', 'Cunha', '1993-07-22 10:10:00', '978901210'),
			(10017, 'Felipe', 'Gomes', '1981-02-13 18:40:00', '989012109'),
			(10018, 'Larissa', 'Araujo', '1995-09-05 13:35:00', '900123008'),
			(10019, 'Thiago', 'Moreira', '1983-04-17 07:55:00', '911234907'),
			(10020, 'Natália', 'Reis', '1990-09-29 14:00:00', '912335674'),
			(10021, 'André', 'Teixeira', '1983-02-15 10:20:00', '923467289'),
			(10022, 'Paula', 'Melo', '1997-07-11 15:30:00', '934567183'),
			(10023, 'Vinícius', 'Souza', '1985-11-22 08:10:00', '945678972'),
			(10024, 'Renata', 'Andrade', '1991-05-16 17:55:00', '956789963'),
			(10025, 'Daniel', 'Nogueira', '1989-08-30 12:45:00', '967890854'),
			(10026, 'Bruna', 'Xavier', '1993-06-07 09:20:00', '978901745'),
			(10027, 'Guilherme', 'Torres', '1980-12-18 18:10:00', '989012636'),
			(10028, 'Amanda', 'Fernandes', '1998-03-25 13:40:00', '900123527'),
			(10029, 'Pedro', 'Duarte', '1984-07-31 07:05:00', '911234418'),
			(10030, 'João', 'Batista', '1995-10-02 14:20:00', '912349309'),
			(10031, 'Carolina', 'Ribeiro', '1987-06-12 09:40:00', '923459210'),
			(10032, 'Samuel', 'Castro', '1996-04-28 18:55:00', '934567321'),
			(10033, 'Tatiana', 'Albuquerque', '1982-08-08 12:30:00', '945678432'),
			(10034, 'Henrique', 'Fonseca', '1999-12-05 07:50:00', '956789543'),
			(10035, 'Larissa', 'Rocha', '1986-05-18 11:35:00', '967890654'),
			(10036, 'Matheus', 'Andrade', '1993-07-29 15:10:00', '978901765'),
			(10037, 'Vanessa', 'Costa', '1981-02-04 08:20:00', '989012876'),
			(10038, 'Ricardo', 'Xavier', '1995-09-15 17:30:00', '900123987'),
			(10039, 'Fernanda', 'Duarte', '1991-03-26 16:40:00', '911234098'),
			(10040, 'Rafaela', 'Ferraz', '1990-07-21 14:20:00', '912340198'),
			(10041, 'Leonardo', 'Machado', '1988-03-19 10:10:00', '923457827'),
			(10042, 'Bruno', 'Silveira', '1995-06-30 17:40:00', '934567922'),
			(10043, 'Tatiane', 'Costa', '1982-09-25 12:30:00', '945678833'),
			(10044, 'Felipe', 'Alves', '1999-02-10 09:50:00', '956789744'),
			(10045, 'Eduarda', 'Fernandes', '1987-11-15 18:20:00', '967890655'),
			(10046, 'Vinícius', 'Martins', '1993-04-07 13:45:00', '978901566'),
			(10047, 'Amanda', 'Rodrigues', '1996-08-29 08:10:00', '989012477'),
			(10048, 'Lucas', 'Pinto', '1981-12-05 16:55:00', '900123388'),
			(10049, 'Carla', 'Vieira', '1994-10-13 11:35:00', '911234299'),
			(10050, 'Renan', 'Cardoso', '1985-07-28 14:40:00', '912349210'),
			(10051, 'Luana', 'Monteiro', '1998-05-18 09:20:00', '923459121'),
			(10052, 'Rodrigo', 'Albuquerque', '1991-03-09 17:30:00', '934567232'),
			(10053, 'Matheus', 'Ribeiro', '1983-09-15 12:10:00', '945678343'),
			(10054, 'Daniele', 'Souza', '1997-11-30 07:55:00', '956789454'),
			(10055, 'Henrique', 'Melo', '1986-06-24 11:45:00', '967890565'),
			(10056, 'Fernanda', 'Nogueira', '1993-02-05 15:25:00', '978901676'),
			(10057, 'Giovana', 'Castro', '1980-08-18 08:30:00', '989012787'),
			(10058, 'Gustavo', 'Torres', '1995-05-21 18:40:00', '900123898'),
			(10059, 'Ana Paula', 'Xavier', '1989-04-10 13:50:00', '911234909'),
			(10060, 'Rafael', 'Dias', '1991-02-22 15:00:00', '912335619'),
			(10061, 'Juliana', 'Lima', '1984-07-07 10:30:00', '923467728'),
			(10062, 'Thiago', 'Pereira', '1993-11-11 17:15:00', '934567837'),
			(10063, 'Camila', 'Oliveira', '1996-01-25 12:40:00', '945678946'),
			(10064, 'Gabriel', 'Ferreira', '1980-05-14 08:20:00', '956789055'),
			(10065, 'Beatriz', 'Almeida', '1999-09-08 18:55:00', '967890164'),
			(10066, 'Fernando', 'Santos', '1987-03-29 13:10:00', '978901273'),
			(10067, 'Paula', 'Rodrigues', '1995-06-16 07:45:00', '989012382'),
			(10068, 'Bruno', 'Monteiro', '1982-10-31 16:35:00', '900123491'),
			(10069, 'Tatiana', 'Costa', '1998-12-12 11:20:00', '911234502'),
			(10070, 'Eduardo', 'Barbosa', '1983-08-21 14:50:00', '912349613'),
			(10071, 'Vanessa', 'Albuquerque', '1997-04-27 09:30:00', '923459724'),
			(10072, 'Rodrigo', 'Nogueira', '1986-09-04 17:45:00', '934567835'),
			(10073, 'Giovana', 'Ribeiro', '1990-01-19 12:55:00', '945678946'),
			(10074, 'Larissa', 'Souza', '1985-05-06 07:50:00', '956789057'),
			(10075, 'Lucas', 'Melo', '1994-03-23 11:35:00', '967890168'),
			(10076, 'Mariana', 'Castro', '1981-11-09 15:20:00', '978901279'),
			(10077, 'Felipe', 'Torres', '1992-07-02 08:45:00', '989012390'),
			(10078, 'Renata', 'Xavier', '1996-02-10 18:50:00', '900123401'),
			(10079, 'Guilherme', 'Dias', '1989-10-30 13:40:00', '911234512'),
			(10080, 'Marcela', 'Ferreira', '1992-04-12 11:30:00', '912348123'),
			(10081, 'Diego', 'Martins', '1986-08-09 16:20:00', '923457892'),
			(10082, 'Bruna', 'Alves', '1993-11-25 08:45:00', '934567921'),
			(10083, 'Samuel', 'Rodrigues', '1984-09-30 17:50:00', '945678834'),
			(10084, 'Tatiane', 'Silva', '1998-07-14 12:15:00', '956789745'),
			(10085, 'Lucas', 'Monteiro', '1989-06-10 09:40:00', '967890656'),
			(10086, 'Gabriela', 'Lima', '1995-05-22 18:05:00', '978901567'),
			(10087, 'Fernando', 'Barbosa', '1981-03-28 13:55:00', '989012478'),
			(10088, 'Paula', 'Nogueira', '1994-12-05 07:30:00', '900123389'),
			(10089, 'Eduardo', 'Ribeiro', '1997-02-19 16:15:00', '911234290'),
			(10090, 'Vanessa', 'Souza', '1983-08-08 10:50:00', '912349201'),
			(10091, 'Thiago', 'Pereira', '1996-09-27 15:10:00', '923459112'),
			(10092, 'Beatriz', 'Torres', '1991-07-03 09:20:00', '934567223'),
			(10093, 'Rodrigo', 'Xavier', '1980-10-15 18:30:00', '945678334'),
			(10094, 'Matheus', 'Castro', '1999-12-02 12:45:00', '956789445'),
			(10095, 'Ana Paula', 'Melo', '1985-05-25 08:20:00', '967890556'),
			(10096, 'Guilherme', 'Oliveira', '1994-03-17 14:40:00', '978901667'),
			(10097, 'Larissa', 'Costa', '1987-11-29 11:35:00', '989012778'),
			(10098, 'Felipe', 'Fernandes', '1993-06-13 17:25:00', '900123889'),
			(10099, 'Renata', 'Dias', '1995-01-04 07:50:00', '911234999'),
			(10100, 'Rafaela', 'Rodrigues', '1990-06-18 14:10:00', '912348765'),
			(10101, 'Leonardo', 'Vieira', '1988-03-22 10:40:00', '923457876'),
			(10102, 'Bruno', 'Almeida', '1995-07-05 17:20:00', '934567987'),
			(10103, 'Tatiane', 'Ferraz', '1982-09-10 12:50:00', '945678698'),
			(10104, 'Felipe', 'Machado', '1999-02-17 09:35:00', '956789509'),
			(10105, 'Eduarda', 'Lima', '1987-11-13 18:45:00', '967890320'),
			(10106, 'Vinícius', 'Santos', '1993-04-02 13:25:00', '978901431'),
			(10107, 'Amanda', 'Pinto', '1996-08-20 08:50:00', '989012542'),
			(10108, 'Lucas', 'Monteiro', '1981-12-09 16:30:00', '900123653'),
			(10109, 'Carla', 'Cardoso', '1994-10-25 11:00:00', '911234764'),
			(10110, 'Renan', 'Albuquerque', '1985-07-12 14:55:00', '912349875'),
			(10111, 'Luana', 'Nogueira', '1998-05-23 09:15:00', '923459986'),
			(10112, 'Rodrigo', 'Xavier', '1991-03-14 17:50:00', '934567197'),
			(10113, 'Matheus', 'Ribeiro', '1983-09-18 12:30:00', '945678308'),
			(10114, 'Daniele', 'Souza', '1997-11-07 07:45:00', '956789419'),
			(10115, 'Henrique', 'Melo', '1986-06-29 11:55:00', '967890530'),
			(10116, 'Fernanda', 'Castro', '1993-02-15 15:40:00', '978901641'),
			(10117, 'Giovana', 'Torres', '1980-08-02 08:35:00', '989012752'),
			(10118, 'Gustavo', 'Dias', '1995-05-10 18:25:00', '900123863'),
			(10119, 'Ana Paula', 'Fernandes', '1989-04-22 13:55:00', '911234974'),
			(10120, 'Rafael', 'Santana', '1992-01-15 14:30:00', '912348112');

INSERT INTO company.preco_delivery (id, nome, preco) VALUES
			(1, 'Centro', 5.50),
			(2, 'Jardins', 6.00),
			(3, 'Bela Vista', 5.80),
			(4, 'Moema', 6.50),
			(5, 'Pinheiros', 5.90),
			(6, 'Vila Madalena', 6.20),
			(7, 'Itaim Bibi', 6.40),
			(8, 'Liberdade', 5.70),
			(9, 'Santa Cecília', 5.60),
			(10, 'Perdizes', 6.00),
			(11, 'Vila Mariana', 5.85),
			(12, 'Butantã', 5.40),
			(13, 'Lapa', 5.30),
			(14, 'Santana', 5.50),
			(15, 'Tatuapé', 5.20),
			(16, 'Vila Prudente', 5.60),
			(17, 'Aclimação', 6.10),
			(18, 'Paraíso', 6.30),
			(19, 'Barra Funda', 5.70),
			(20, 'Ipiranga', 5.50),
			(21, 'Anália Franco', 6.20),
			(22, 'São Mateus', 5.10),
			(23, 'Sapopemba', 5.00),
			(24, 'Freguesia do Ó', 5.40),
			(25, 'Casa Verde', 5.30),
			(26, 'Brasilândia', 4.90),
			(27, 'Campo Limpo', 4.80),
			(28, 'Capão Redondo', 4.75),
			(29, 'Grajaú', 4.60),
			(30, 'Cidade Tiradentes', 4.50),
			(31, 'São Miguel Paulista', 5.00),
			(32, 'Guaianases', 4.95),
			(33, 'Pirituba', 5.25),
			(34, 'Mandaqui', 5.35),
			(35, 'Tremembé', 5.50),
			(36, 'Vila Guilherme', 5.40),
			(37, 'Jabaquara', 5.60),
			(38, 'Vila Leopoldina', 5.70),
			(39, 'Rio Pequeno', 5.30),
			(40, 'Morumbi', 6.50);  

INSERT INTO company.viagem_delivery (id_motoqueiro, percurso_em_km, data, id_bairro) VALUES
(10000, 12.3, '2024-01-02', 5),
(10000, 9.1, '2024-01-04', 17),
(10001, 15.8, '2024-01-06', 30),
(10001, 7.6, '2024-01-08', 27),
(10002, 14.5, '2024-01-10', 7),
(10002, 8.4, '2024-01-12', 24),
(10002, 11.2, '2024-01-14', 19),
(10003, 9.9, '2024-01-16', 12),
(10003, 13.6, '2024-01-18', 28),
(10004, 7.7, '2024-01-20', 39),
(10004, 11.4, '2024-01-22', 26),
(10004, 8.2, '2024-01-24', 15),
(10005, 14.9, '2024-01-26', 20),
(10005, 16.3, '2024-01-28', 2),
(10006, 9.7, '2024-01-30', 31),
(10006, 6.9, '2024-01-01', 13),
(10007, 12.7, '2024-01-03', 22),
(10007, 12.7, '2024-01-03', 22),
(10007, 10.6, '2024-01-05', 16),
(10008, 14.2, '2024-01-07', 9),
(10008, 7.8, '2024-01-09', 11),
(10009, 15.5, '2024-01-11', 35),
(10009, 8.9, '2024-01-13', 10),
(10010, 11.3, '2024-01-15', 29),
(10010, 7.1, '2024-01-17', 18),
(10011, 12.0, '2024-01-19', 37),
(10011, 13.8, '2024-01-21', 40),
(10012, 9.8, '2024-01-23', 21),
(10012, 12.3, '2024-01-25', 14),
(10013, 7.5, '2024-01-27', 34),
(10013, 14.2, '2024-01-29', 38),
(10014, 10.9, '2024-01-31', 32),
(10014, 6.7, '2024-01-02', 26),
(10015, 15.6, '2024-01-04', 33),
(10016, 13.2, '2024-01-06', 6),
(10016, 8.5, '2024-01-08', 19),
(10017, 15.9, '2024-01-10', 31),
(10017, 7.4, '2024-01-12', 22),
(10018, 14.1, '2024-01-14', 9),
(10018, 6.8, '2024-01-16', 23),
(10019, 11.7, '2024-01-18', 36),
(10019, 9.6, '2024-01-20', 14),
(10020, 13.4, '2024-01-22', 27),
(10020, 7.8, '2024-01-24', 25),
(10030, 11.1, '2024-01-02', 12),
(10030, 6.5, '2024-01-04', 28),
(10030, 15.6, '2024-01-07', 23),
(10031, 12.4, '2024-01-01', 8),
(10031, 9.2, '2024-01-03', 17),
(10031, 15.7, '2024-01-05', 41),
(10031, 7.6, '2024-01-07', 23),
(10032, 14.8, '2024-01-02', 3),
(10032, 7.3, '2024-01-04', 35),
(10032, 10.5, '2024-01-06', 47),
(10033, 9.1, '2024-01-01', 11),
(10033, 13.5, '2024-01-03', 26),
(10033, 7.9, '2024-01-06', 50),
(10034, 11.9, '2024-01-02', 28),
(10034, 8.6, '2024-01-04', 7),
(10034, 14.2, '2024-01-07', 20),
(10035, 16.6, '2024-01-01', 5),
(10035, 9.8, '2024-01-03', 31),
(10035, 6.7, '2024-01-05', 39),
(10035, 12.3, '2024-01-08', 16),
(10036, 10.2, '2024-01-02', 13),
(10036, 14.7, '2024-01-04', 22),
(10036, 7.5, '2024-01-06', 46),
(10037, 15.3, '2024-01-01', 44),
(10037, 8.1, '2024-01-03', 18),
(10037, 10.6, '2024-01-05', 32),
(10038, 6.5, '2024-01-02', 25),
(10038, 11.4, '2024-01-04', 10),
(10038, 13.9, '2024-01-07', 42),
(10039, 9.9, '2024-01-01', 37),
(10039, 12.2, '2024-01-03', 15),
(10039, 7.2, '2024-01-05', 21),
(10039, 14.5, '2024-01-08', 50),
(10040, 11.0, '2024-01-02', 30),
(10040, 6.9, '2024-01-04', 29),
(10040, 15.4, '2024-01-07', 33),
(10041, 13.2, '2024-01-01', 6),
(10041, 8.5, '2024-01-03', 17),
(10041, 15.9, '2024-01-05', 31),
(10041, 7.4, '2024-01-07', 22),
(10042, 14.1, '2024-01-02', 9),
(10042, 6.8, '2024-01-04', 33),
(10042, 11.7, '2024-01-06', 46),
(10043, 9.6, '2024-01-01', 14),
(10043, 13.4, '2024-01-03', 27),
(10043, 7.8, '2024-01-06', 49),
(10044, 12.7, '2024-01-02', 10),
(10044, 8.9, '2024-01-04', 42),
(10044, 15.3, '2024-01-07', 20),
(10045, 16.1, '2024-01-01', 5),
(10045, 9.2, '2024-01-03', 30),
(10045, 6.5, '2024-01-05', 44),
(10045, 11.9, '2024-01-08', 19),
(10046, 10.5, '2024-01-02', 11),
(10046, 14.8, '2024-01-04', 25),
(10046, 7.7, '2024-01-06', 47),
(10047, 15.6, '2024-01-01', 50),
(10047, 8.3, '2024-01-03', 28),
(10047, 10.9, '2024-01-05', 37),
(10048, 7.1, '2024-01-02', 3),
(10048, 12.0, '2024-01-04', 35),
(10048, 13.9, '2024-01-07', 41),
(10049, 9.9, '2024-01-01', 39),
(10049, 12.5, '2024-01-03', 21),
(10049, 7.4, '2024-01-05', 29),
(10049, 14.3, '2024-01-08', 16),
(10050, 10.8, '2024-01-02', 32),
(10050, 6.9, '2024-01-04', 24),
(10050, 15.4, '2024-01-07', 9),
(10050, 10.8, '2024-01-02', 32),
(10050, 6.9, '2024-01-02', 24),
(10050, 15.4, '2024-01-06', 9),
(10051, 14.4, '2024-01-01', 12),
(10051, 9.1, '2024-01-03', 25),
(10051, 15.2, '2024-01-05', 31),
(10051, 7.8, '2024-01-07', 36),
(10052, 13.7, '2024-01-02', 8),
(10052, 7.2, '2024-01-04', 33),
(10052, 10.5, '2024-01-06', 19),
(10053, 9.9, '2024-01-01', 5),
(10053, 12.4, '2024-01-03', 20),
(10053, 7.6, '2024-01-06', 37),
(10054, 11.2, '2024-01-02', 14),
(10054, 8.3, '2024-01-04', 29),
(10054, 14.7, '2024-01-07', 40),
(10055, 16.2, '2024-01-01', 3),
(10055, 9.5, '2024-01-03', 26),
(10055, 6.9, '2024-01-05', 32),
(10055, 12.6, '2024-01-08', 18),
(10056, 10.3, '2024-01-02', 17),
(10056, 14.8, '2024-01-04', 7),
(10056, 7.5, '2024-01-06', 22),
(10057, 15.1, '2024-01-01', 30),
(10057, 8.7, '2024-01-03', 9),
(10057, 10.6, '2024-01-05', 39),
(10058, 7.0, '2024-01-02', 27),
(10058, 12.5, '2024-01-04', 14),
(10058, 13.9, '2024-01-07', 25),
(10059, 10.1, '2024-01-01', 35),
(10059, 12.6, '2024-01-03', 18),
(10059, 7.9, '2024-01-05', 11),
(10059, 14.4, '2024-01-08', 38),
(10060, 11.0, '2024-01-02', 23),
(10060, 6.5, '2024-01-04', 6),
(10060, 15.3, '2024-01-07', 37),
(10061, 13.2, '2024-01-01', 2),
(10061, 8.5, '2024-01-03', 12),
(10061, 15.9, '2024-01-05', 29),
(10061, 7.4, '2024-01-07', 40),
(10062, 14.1, '2024-01-02', 7),
(10062, 6.8, '2024-01-04', 22),
(10062, 11.7, '2024-01-06', 33),
(10063, 9.6, '2024-01-01', 19),
(10063, 13.4, '2024-01-03', 5),
(10063, 7.8, '2024-01-06', 26),
(10064, 12.7, '2024-01-02', 15),
(10064, 8.9, '2024-01-04', 32),
(10064, 15.3, '2024-01-07', 36),
(10065, 16.1, '2024-01-01', 9),
(10065, 9.2, '2024-01-03', 27),
(10065, 6.5, '2024-01-05', 11),
(10065, 11.9, '2024-01-08', 38),
(10066, 10.5, '2024-01-02', 23),
(10066, 14.8, '2024-01-04', 6),
(10066, 7.7, '2024-01-06', 37),
(10067, 15.6, '2024-01-01', 40),
(10067, 8.3, '2024-01-03', 25),
(10067, 10.9, '2024-01-05', 19),
(10068, 7.1, '2024-01-02', 12),
(10068, 12.0, '2024-01-04', 30),
(10068, 13.9, '2024-01-07', 14),
(10069, 9.9, '2024-01-01', 29),
(10069, 12.5, '2024-01-03', 7),
(10069, 7.4, '2024-01-05', 22),
(10069, 14.3, '2024-01-08', 36),
(10070, 10.8, '2024-01-02', 6),
(10070, 6.9, '2024-01-04', 15),
(10070, 15.4, '2024-01-07', 33),
(10070, 10, '2024-01-03', 32),
(10071, 14.4, '2024-01-01', 12),
(10071, 9.1, '2024-01-03', 25),
(10071, 15.2, '2024-01-05', 31),
(10071, 7.8, '2024-01-07', 36),
(10072, 13.7, '2024-01-02', 8),
(10072, 7.2, '2024-01-04', 33),
(10072, 10.5, '2024-01-06', 19),
(10073, 9.9, '2024-01-01', 5),
(10073, 12.4, '2024-01-03', 20),
(10073, 7.6, '2024-01-06', 37),
(10074, 11.2, '2024-01-02', 14),
(10074, 8.3, '2024-01-04', 29),
(10074, 14.7, '2024-01-07', 40),
(10075, 16.2, '2024-01-01', 3),
(10075, 9.5, '2024-01-03', 26),
(10075, 6.9, '2024-01-05', 32),
(10075, 12.6, '2024-01-08', 18),
(10076, 10.3, '2024-01-02', 17),
(10076, 14.8, '2024-01-04', 7),
(10076, 7.5, '2024-01-06', 22),
(10077, 15.1, '2024-01-01', 30),
(10077, 8.7, '2024-01-03', 9),
(10077, 10.6, '2024-01-05', 39),
(10078, 7.0, '2024-01-02', 27),
(10078, 12.5, '2024-01-04', 14),
(10078, 13.9, '2024-01-07', 25),
(10079, 10.1, '2024-01-01', 35),
(10079, 12.6, '2024-01-03', 18),
(10079, 7.9, '2024-01-05', 11),
(10079, 14.4, '2024-01-08', 38),
(10080, 11.0, '2024-01-02', 23),
(10080, 6.5, '2024-01-04', 6),
(10080, 15.3, '2024-01-07', 37),
(10081, 13.2, '2024-01-01', 2),
(10081, 8.5, '2024-01-03', 12),
(10081, 15.9, '2024-01-05', 29),
(10081, 7.4, '2024-01-07', 40),
(10082, 14.1, '2024-01-02', 7),
(10082, 6.8, '2024-01-04', 22),
(10082, 11.7, '2024-01-06', 33),
(10083, 9.6, '2024-01-01', 19),
(10083, 13.4, '2024-01-03', 5),
(10083, 7.8, '2024-01-06', 26),
(10084, 12.7, '2024-01-02', 15),
(10084, 8.9, '2024-01-04', 32),
(10084, 15.3, '2024-01-07', 36),
(10085, 16.1, '2024-01-01', 9),
(10085, 9.2, '2024-01-03', 27),
(10085, 6.5, '2024-01-05', 11),
(10085, 11.9, '2024-01-08', 38),
(10086, 10.5, '2024-01-02', 23),
(10086, 14.8, '2024-01-04', 6),
(10086, 7.7, '2024-01-06', 37),
(10087, 15.6, '2024-01-01', 40),
(10087, 8.3, '2024-01-03', 25),
(10087, 10.9, '2024-01-05', 19),
(10088, 7.1, '2024-01-02', 12),
(10088, 12.0, '2024-01-04', 30),
(10088, 13.9, '2024-01-07', 14),
(10089, 9.9, '2024-01-01', 29),
(10089, 12.5, '2024-01-03', 7),
(10089, 7.4, '2024-01-05', 22),
(10089, 14.3, '2024-01-08', 36),
(10090, 10.8, '2024-01-02', 6),
(10090, 6.9, '2024-01-04', 15),
(10090, 15.4, '2024-01-07', 33),
(10091, 13.2, '2024-01-01', 6),
(10091, 8.5, '2024-01-03', 17),
(10091, 15.9, '2024-01-05', 31),
(10091, 7.4, '2024-01-07', 22),
(10092, 14.1, '2024-01-02', 9),
(10092, 6.8, '2024-01-04', 33),
(10092, 11.7, '2024-01-06', 40),
(10093, 9.6, '2024-01-01', 14),
(10093, 13.4, '2024-01-03', 27),
(10093, 7.8, '2024-01-06', 19),
(10094, 12.7, '2024-01-02', 10),
(10094, 8.9, '2024-01-04', 32),
(10094, 15.3, '2024-01-07', 36),
(10095, 16.1, '2024-01-01', 5),
(10095, 9.2, '2024-01-03', 30),
(10095, 6.5, '2024-01-05', 11),
(10095, 11.9, '2024-01-08', 38),
(10096, 10.5, '2024-01-02', 23),
(10096, 14.8, '2024-01-04', 6),
(10096, 7.7, '2024-01-06', 37),
(10097, 15.6, '2024-01-01', 40),
(10097, 8.3, '2024-01-03', 25),
(10097, 10.9, '2024-01-05', 19),
(10098, 7.1, '2024-01-02', 12),
(10098, 12.0, '2024-01-04', 30),
(10098, 13.9, '2024-01-07', 14),
(10099, 9.9, '2024-01-01', 29),
(10099, 12.5, '2024-01-03', 7),
(10099, 7.4, '2024-01-05', 22),
(10099, 14.3, '2024-01-08', 36),
(10100, 10.8, '2024-01-02', 6),
(10100, 6.9, '2024-01-04', 15),
(10100, 15.4, '2024-01-07', 33),
(10101, 12.5, '2024-01-02', 5),
(10101, 9.1, '2024-01-04', 17),
(10102, 15.8, '2024-01-06', 30),
(10102, 7.6, '2024-01-08', 27),
(10103, 14.5, '2024-01-10', 7),
(10103, 8.4, '2024-01-12', 24),
(10103, 11.2, '2024-01-14', 19),
(10104, 9.9, '2024-01-16', 12),
(10104, 13.6, '2024-01-18', 28),
(10105, 7.7, '2024-01-20', 39),
(10105, 11.4, '2024-01-22', 26),
(10105, 8.2, '2024-01-24', 15),
(10106, 14.9, '2024-01-26', 20),
(10106, 16.3, '2024-01-28', 2),
(10107, 9.7, '2024-01-30', 31),
(10107, 6.9, '2024-01-01', 13),
(10108, 12.7, '2024-01-03', 22),
(10108, 10.6, '2024-01-05', 16),
(10109, 14.2, '2024-01-07', 9),
(10109, 7.8, '2024-01-09', 11),
(10110, 15.5, '2024-01-11', 35),
(10110, 8.9, '2024-01-13', 10),
(10111, 11.3, '2024-01-15', 29),
(10111, 7.1, '2024-01-17', 18),
(10112, 12.0, '2024-01-19', 37),
(10112, 13.8, '2024-01-21', 40),
(10113, 9.8, '2024-01-23', 21),
(10113, 12.3, '2024-01-25', 14),
(10114, 7.5, '2024-01-27', 34),
(10114, 14.2, '2024-01-29', 38),
(10115, 10.9, '2024-01-31', 32),
(10115, 6.7, '2024-01-02', 26),
(10116, 15.6, '2024-01-04', 33),
(10117, 13.2, '2024-01-06', 6),
(10117, 8.5, '2024-01-08', 19),
(10118, 15.9, '2024-01-10', 31),
(10118, 7.4, '2024-01-12', 22),
(10119, 14.1, '2024-01-14', 9),
(10119, 6.8, '2024-01-16', 23),
(10120, 11.7, '2024-01-18', 36),
(10120, 9.6, '2024-01-20', 14);



-- Fazendo um JOIN entre as tabelas
SELECT * FROM company.cadastros_delivery;
SELECT * FROM company.viagem_delivery;
SELECT * FROM company.preco_delivery;
SHOW TABLES;

-- Fazendo o JOIN entre as tabelas, criando a coluna receita_total, agrupando pela soma e ordenando de modo decrescente
SELECT vd.id_motoqueiro, cd.primeiro_nome, cd.ultimo_nome, 
       SUM(vd.percurso_em_km * pd.preco) AS receita_total
FROM company.viagem_delivery AS vd
JOIN company.cadastros_delivery AS cd
    ON vd.id_motoqueiro = cd.id
JOIN company.preco_delivery AS pd
    ON vd.id_bairro = pd.id
GROUP BY vd.id_motoqueiro, cd.primeiro_nome, cd.ultimo_nome
ORDER BY receita_total DESC
LIMIT 100;

-- DESAFIO 6: ​Você possui uma tabela chamada attendance com as colunas id, date e present.
-- id: id do funcionário
-- date: data de presença.
-- present: Esta coluna tem o valor de 1 ou 0, onde 1 representa presente, e 0 representa ausente.
-- Agora, escreva uma consulta SQL para encontrar o ID do funcionário que veio ao escritório por mais dias consecutivos.

DROP TABLE IF EXISTS company.attendance;
CREATE TABLE company.attendance(
			id INT,
            dt_presença DATETIME,
            present INT
);
INSERT INTO company.attendance (id, dt_presença, present) VALUES
(1001, '2024-06-01', 1),
(1001, '2024-06-02', 1),
(1001, '2024-06-03', 0),
(1001, '2024-06-04', 1),
(1001, '2024-06-05', 1),
(1002, '2024-06-01', 1),
(1002, '2024-06-02', 0),
(1002, '2024-06-03', 1),
(1002, '2024-06-04', 1),
(1002, '2024-06-05', 1),
(1003, '2024-06-01', 0),
(1003, '2024-06-02', 0),
(1003, '2024-06-03', 1),
(1003, '2024-06-04', 0),
(1003, '2024-06-05', 1),
(1004, '2024-06-01', 1),
(1004, '2024-06-02', 1),
(1004, '2024-06-03', 1),
(1004, '2024-06-04', 1),
(1004, '2024-06-05', 1);

-- Presenças totais
SELECT id, SUM(present) AS total_presenca 
FROM company.attendance
GROUP BY id
ORDER BY total_presenca DESC;


-- Presença consecutiva
WITH attendance_sequences AS (
    SELECT id, dt_presença, present,
           dt_presença - INTERVAL ROW_NUMBER() OVER (PARTITION BY id ORDER BY dt_presença) DAY AS group_id
    FROM company.attendance
    WHERE present = 1
)
SELECT id, COUNT(*) AS max_dias_consecutivos
FROM attendance_sequences
GROUP BY id, group_id
ORDER BY max_dias_consecutivos DESC
LIMIT 1;
