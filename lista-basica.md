```sql
DROP TABLE IF EXISTS company.cadastro_mkt;
CREATE TABLE company.cadastro_mkt (
				ID INT PRIMARY KEY AUTO_INCREMENT,
                CPF CHAR(9),
                Primeiro_nome VARCHAR(50),
                Idade INT,
                Renda DECIMAL(10,2),
                Profissão VARCHAR(100)
);

SELECT * FROM company.cadastro_mkt;
INSERT INTO company.cadastro_mkt (CPF, Primeiro_nome, Idade, Renda, Profissão) VALUES
				('123456789', 'Ana', 25, 3500.50, 'Engenheira Civil'),
				('987654321', 'Carlos', 67, 4200.75, 'Professor'),
				('456789123', 'Beatriz', 22, 2800.00, 'Designer Gráfico'),
				('654123789', 'Fernando', 29, 5000.25, 'Desenvolvedor de Software'),
				('321987654', 'Juliana', 33, 6200.80, 'Médica'),
				('789321456', 'Rafael', 27, 3700.90, 'Analista Financeiro'),
				('159753258', 'Mariana', 24, 3100.60, 'Advogada'),
				('753951456', 'Lucas', 31, 4500.40, 'Contador'),
				('852963741', 'Sofia', 28, 3900.30, 'Psicóloga'),
				('741258963', 'Gustavo', 26, 3200.10, 'Arquiteto'),
				('369258147', 'Camila', 23, 2800.70, 'Jornalista'),
				('147852369', 'Eduardo', 0, 5400.85, 'Gerente de Projetos'),
				('258147369', 'Letícia', 21, 2600.45, 'Publicitária'),
				('963852741', 'Rodrigo', 32, 4700.55, 'Administrador'),
				('852741963', 'Tatiane', 29, 4000.20, 'Farmacêutica'),
				('112233445', 'Gabriel', 27, 3800.60, 'Engenheiro de Produção'),
				('556677889', 'Alice', 30, 4400.75, 'Cientista de Dados'),
				('334455667', 'Felipe', 29, 5100.40, 'Gerente de TI'),
				('778899112', 'Larissa', 26, 3300.15, 'Fisioterapeuta'),
				('991122334', 'Thiago', 34, 6000.50, 'Dentista'),
				('223344556', 'Natália', 25, 3600.80, 'Analista de Recursos Humanos'),
				('667788990', 'André', 31, 4800.30, 'Economista'),
				('445566778', 'Paula', 28, 4100.20, 'Engenheira Química'),
				('889900112', 'Vinícius', 22, 2700.90, 'Desenvolvedor Júnior'),
				('990011223', 'Renata', 33, 5300.75, 'Diretora Comercial'),
				('331122445', 'Daniel', 0, 2900.60, 'Assistente Administrativo'),
				('776655443', 'Bruna', 29, 4000.55, 'Consultora de Vendas'),
				('554433221', 'Guilherme', 35, 6200.80, 'Advogado Corporativo'),
				('110099887', 'Amanda', 23, 3100.45, 'Marketing Digital'),
				('221133445', 'Pedro', 27, 3700.20, 'Analista de Logística'),
				('332211445', 'Marta', 29, 4600.80, 'Engenheira Ambiental'),
				('998877665', 'Ricardo', 31, 5200.90, 'Contador'),
				('776622993', 'Vanessa', 28, 3900.75, 'Fisioterapeuta'),
				('553344221', 'Júlio', 26, 3200.20, 'Arquiteto'),
				('774499882', 'Tatiana', 24, 2800.50, 'Designer UX'),
				('442266775', 'Jorge', 32, 5700.85, 'Gerente de Operações'),
				('991188776', 'Luciana', 33, 6100.40, 'Advogada Trabalhista'),
				('553377221', 'Victor', 29, 4700.30, 'Analista de Sistemas'),
				('880077665', 'Fernanda', 27, 3500.90, 'Nutricionista'),
				('221144889', 'Rogério', 35, 6500.75, 'Diretor Financeiro'),
				('331188554', 'Débora', 25, 3200.40, 'Terapeuta Ocupacional'),
				('663322115', 'Samuel', 23, 3100.70, 'Analista de Marketing'),
				('992255337', 'Carol', 30, 4500.60, 'Engenheira Mecânica'),
				('775511998', 'Antônio', 31, 5000.45, 'Analista Jurídico'),
				('445599887', 'Vera', 29, 4300.20, 'Gerente Comercial'),
				('998811443', 'Alberto', 26, 3300.35, 'Engenheiro de Software'),
				('221155789', 'Raquel', 27, 3500.50, 'Arquiteta de Dados'),
				('778855334', 'Camilo', 34, 6100.75, 'Advogado Criminalista'),
				('995577332', 'Cíntia', 22, 2900.60, 'Designer de Moda'),
				('448877665', 'Osvaldo', 35, 6800.90, 'CEO de Startup'),
				('774411228', 'Flávia', 28, 4200.75, 'Contadora'),
				('665533221', 'Miguel', 29, 5100.40, 'Especialista em TI'),
				('110022334', 'Patrícia', 23, 3000.30, 'Terapeuta Holística'),
				('885566774', 'Estela', 31, 4900.85, 'Engenheira de Produção'),
				('125487963', 'Otávio', 29, 5200.45, 'Engenheiro Eletricista'),
				('985612347', 'Bárbara', 31, 4700.60, 'Arquiteta Urbanista'),
				('456321789', 'Cláudio', 27, 3800.75, 'Desenvolvedor Mobile'),
				('654789123', 'Natália', 23, 3100.80, 'Bióloga'),
				('321654987', 'Leandro', 35, 6000.20, 'Médico Veterinário'),
				('789654123', 'Sandra', 30, 4100.40, 'Analista de RH'),
				('159753846', 'Bruno', 26, 3500.55, 'Marketing Digital'),
				('753951852', 'Fernanda', 28, 4200.10, 'Advogada Criminalista'),
				('852963147', 'Hugo', 32, 5500.90, 'Gerente de Produto'),
				('741258357', 'Vanessa', 25, 3300.35, 'Psicóloga Clínica'),
				('369258741', 'Leonardo', 22, 2900.25, 'Editor de Vídeo'),
				('147852753', 'Juliana', 29, 4600.50, 'Fonoaudióloga'),
				('258147852', 'Marcelo', 33, 5800.70, 'Cientista de Dados'),
				('963852753', 'Patrícia', 27, 3900.80, 'Terapeuta Ocupacional'),
				('852741753', 'Thiago', 31, 4900.30, 'Professor de Matemática'),
				('112233559', 'Tatiane', 24, 3000.45, 'Produtora Cultural'),
				('556677881', 'Emanuel', 35, 6200.60, 'Engenheiro Mecânico'),
				('334455669', 'Isabela', 28, 4300.20, 'Analista de Comércio Exterior'),
				('778899113', 'Rodrigo', 30, 5200.55, 'Gestor de Projetos'),
				('991122335', 'Lívia', 26, 3700.35, 'Nutricionista Esportiva'),
				('223344557', 'Murilo', 25, 3400.80, 'Geólogo'),
				('667788991', 'Eduarda', 29, 4600.95, 'Jornalista Política'),
				('445566779', 'Renan', 31, 5100.10, 'Administrador Hospitalar'),
				('889900113', 'Cristiane', 23, 3200.75, 'Designer UX/UI'),
				('990011224', 'Danilo', 34, 5800.45, 'Analista de Segurança da Informação'),
				('331122446', 'Natasha', 27, 4000.60, 'Especialista em Recursos Humanos'),
				('776655444', 'Raphael', 22, 2800.30, 'Fotógrafo Publicitário'),
				('554433222', 'Mônica', 35, 6200.85, 'Diretora de Arte'),
				('110099888', 'Igor', 26, 3300.55, 'Engenheiro de Software'),
				('221133446', 'Raquel', 28, 3900.90, 'Advogada Trabalhista'),
				('332211446', 'Felipe', 32, 5500.20, 'Gerente de TI'),
				('998877666', 'Silvana', 24, 3100.75, 'Pedagoga'),
				('776622994', 'Caio', 30, 5200.30, 'Consultor Financeiro'),
				('553344222', 'Elaine', 27, 3700.50, 'Especialista em Comunicação'),
				('774499883', 'Luiz', 31, 4900.15, 'Gestor de Recursos Humanos'),
				('442266776', 'Carina', 29, 4600.90, 'Arquiteta de Interiores'),
				('991188777', 'Matheus', 35, 6100.40, 'Fisioterapeuta Neurológico'),
				('553377222', 'Viviane', 23, 2800.70, 'Pesquisadora Científica'),
				('880077666', 'Diego', 27, 3500.80, 'Gestor Ambiental'),
        ('112334557', 'Esther', 28, 3900.50, 'Engenheira de Software'),
				('559988776', 'Alessandro', 31, 4800.30, 'Consultor Empresarial'),
				('334455668', 'Verônica', 26, 3500.80, 'Nutricionista Clínica'),
				('778899114', 'Samuel', 30, 5100.25, 'Desenvolvedor Backend'),
				('991122336', 'Jéssica', 27, 4200.70, 'Pesquisadora de Mercado'),
				('223344558', 'Márcio', 35, 6000.90, 'Especialista em Marketing Digital'),
				('667788992', 'Elaine', 29, 4600.40, 'Arquiteta Urbanista');

-- DESAFIO 1: ​A área de telemarketing está organizando uma campanha e precisa que você levante alguns dados 
-- para que eles consigam entrar em contato com os clientes da empresa. À partir de uma tabela chamada 'cadastro' 
-- selecione todos os clientes que estão localizados nela e as informações das colunas 'Id', 'CPF', 'Primeiro_Nome', 'Idade'.

SELECT Id, CPF, Primeiro_nome, Idade
FROM company.cadastro_mkt;

-- DESAFIO 2: ​A área de telemarketing quer que o arquivo esteja ordenado de forma ascendente pela idade, i.e., 
-- contendo os mais novos nas primeiras linhas e os mais velhos nas últimas. 
-- Realize este ajuste na consulta feita no desafio 1.

SELECT Id, CPF, Primeiro_nome, Idade
FROM company.cadastro_mkt
ORDER BY Idade ASC;

-- DESAFIO 3: ​Parece haver um problema na tabela 'cadastro' do desafio 1. Como uma forma de estudar uma amostra dela, 
-- você decide pegar somente as primeiras 20 linhas. Escreva uma consulta semelhante ao que foi feito no desafio 1, 
-- mas contendo apenas as 20 primeiras linhas.

SELECT Id, CPF, Primeiro_nome
FROM company.cadastro_mkt
LIMIT 20;

-- DESAFIO 4: ​Depois de muito investigar, você viu que não há nenhum problema na tabela, somente um cadastro mal feito, algo bem pontual. 
-- Delete o cadastro de Id número 100.

DELETE FROM company.cadastro_mkt
WHERE Id = 100;

SELECT * FROM company.cadastro_mkt;

-- ​DESAFIO 5: ​Após eliminar o cadastro incorreto do Id de número 100 e reescrever a consulta do desafio 1, 
-- você agora precisa passar para seu chefe qual a idade média dos clientes da empresa. 
-- Escreva a query que realiza essa consulta.

SELECT ROUND(AVG(Idade),0) AS Avg_Idade
FROM company.cadastro_mkt;

-- DESAFIO 6: A empresa deseja saber quantos clientes são maiores de idade. Conte o número de clientes na tabela 
-- 'cadastro' que têm 18 anos ou mais.​ Retorne a coluna com a contagem com o nome 'Maior_de_Idade​'.

SELECT COUNT(*) AS Maior_de_Idade FROM company.cadastro_mkt
WHERE Idade >= 18;

-- DESAFIO 7: A área financeira precisa que você identifique na tabela 'cadastro' quantos clientes têm entre 30 e 40
-- Escreva uma query para contar esses clientes.​ A coluna de contagem deve ter o nome "Qtd_Clientes_30_e_40".

SELECT COUNT(*) AS Qtd_Clientes_30_a_40
FROM company.cadastro_mkt
WHERE Idade BETWEEN 30 AND 40;

-- DESAFIO 8: Verifique a distribuição de clientes por faixa etária agrupando-os em 'menores de 18', '18 a 65' e 
-- 'maiores de 65'.​ Em outras palavras, conte quantos clientes temos nessas faixas, retornando essas faixas em uma 
-- coluna chamada Faixa_Etaria e a quantidade de clientes na coluna Qtd_Clientes.

SELECT 
	CASE WHEN Idade < 18 THEN "Menores de 18"
		 WHEN Idade > 18 AND Idade < 65 THEN "18 a 65"
         ELSE "Maiores de 65"
	END AS Faixa_Etaria,
    COUNT(*) AS Qtd_Clientes
FROM company.cadastro_mkt
GROUP BY Faixa_Etaria    
;   

SELECT * FROM company.cadastro_mkt
WHERE Idade > 65;

-- No caso nossa base tem 2 menores de 18 e 1 maior de 65.

-- DESAFIO 9: A área de marketing quer enviar promoções apenas para os 10 clientes mais jovens. 
-- Selecione os Ids e Primeiros Nomes dos 10 clientes mais jovens.

SELECT * FROM company.cadastro_mkt
ORDER BY Idade ASC
LIMIT 10;

-- DESAFIO 10: Alguns clientes foram cadastrados erroneamente com 'Idade' igual a zero. 
-- Encontre esses clientes e exiba seus Ids e Primeiros Nomes.

SELECT ID, Primeiro_nome FROM company.cadastro_mkt
WHERE Idade = 0;
