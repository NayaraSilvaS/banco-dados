# Pokémon

Há mais de 10 anos, crianças do mundo inteiro vêm descobrindo o mundo encantado dos Pokémon. Hoje, a família de produtos Pokémon inclui videogames, o jogo Pokémon Estampas Ilustradas, a série de TV animada, filmes, brinquedos e muito mais. Muitos pais acreditam que o Pokémon Estampas Ilustradas e os videogames do Pokémon estimulam seus filhos a aprender a ler, já que a leitura é indispensável na maioria dos jogos do Pokémon. Os jogos também estimulam o pensamento estratégico e, em muitos casos, habilidades matemáticas básicas. O Pokémon valoriza muito o espírito esportivo e o respeito pelos outros jogadores.

## O que são Pokémon?

Pokémon são criaturas de todas as formas e tamanhos que convivem com os humanos na natureza. Na grande maioria, os Pokémon não falam, exceto para proferir seus nomes. Os Pokémon são criados e comandados por seus donos (os chamados "Treinadores"). No decorrer das aventuras, os Pokémon crescem e ganham experiência, podendo até mesmo evoluir para Pokémon mais fortes. Alguns Pokémon, como Pikachu, Piplup e Charizard, possuem papéis de destaque na série de videogames, no jogo Estampas Ilustradas e nos programas de TV, mas eles são apenas algumas das quase 500 criaturas que habitam o universo dos Pokémon.

**Fonte:** [Webiste Oficial - Pokémon](https://www.pokemon.com/br/guia-para-pais/)


## Ponto de Partida

Para começar esse exercício, você deverá: 

* 1. Pegar o arquivo `pokedex_create_v1.sql`, disponível na pasta [data](data/)
* 2. Abrir o software [MySQL](https://www.mysql.com/products/workbench/)
* 3. Exectuar o script para importar um novo banco de dados 


## Resumo do Projeto

Para este projeto, sua tarefa é criar consultas (queries), usando as técnicas da [Linguagem de Consulta de Dados](https://github.com/profdiegoaugusto/banco-dados/tree/master/mysql/linguagem-consulta-dados) no banco de dados `pokedex` do universo Pokémon. O esquema do banco de dados possui apenas uma tabela chamada `Pokémon`, com as seguintes colunas:

| Coluna          | Descrição                                                                                                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| numero          | Chave Primária: o número do Pokémon no Pokedex Nacional                                                                                                                                                                          |
| nome            | Nome do Pokémon                                                                                                                                                                                                                  |
| tipo1           | Todas as criaturas Pokémon e seus movimentos recebem determinados tipos. Cada tipo tem vários pontos fortes e fracos no ataque e na defesa, ou seja, cada Pokémon tem um tipo que determina sua fraqueza/resistência aos ataques |
| tipo2           | O tipo secundário do Pokémon caso ele possua                                                                                                                                                                                     |
| total           | Soma de todas as estatísticas básicas (Pontos de Vida, Ataque, Defesa, Ataque Especial, Defesa Especial e Velocidade)                                                                                                            |
| hp              | HP (Hit Points ou Health Points), define quanto dano um Pokémon pode suportar antes de desmaiar                                                                                                                                  |
| ataque          | O ataque base do Pokémon                                                                                                                                                                                                         |
| defesa          | A defesa base do Pokémon                                                                                                                                                                                                         |
| ataque_especial | O ataque especial base do Pokémon                                                                                                                                                                                                |
| defesa_especial | A defesa especial base do Pokémon                                                                                                                                                                                                |
| velocidade      | A velocidade base do Pokémon                                                                                                                                                                                                     |
| geracao         | Número da geração em que o Pokémon foi introduzido                                                                                                                                                                               |
| lendario        | Valor Booleano que indica se o Pokémon é lendário ou não                                                                                                                                                                         |
| cor             | A cor do Pokémon                                                                                                                                                                                                                 |
| altura_m        | Altura em metros do Pokémon                                                                                                                                                                                                      |
| peso_kg         | Peso em Kilos do Pokémon                                                                                                                                                                                                         |
| taxa_captura | A taxa de captura do Pokémon é um número entre 0 e 255, quanto maior, melhor |


## 1. Exercícios de Consultas


1. Selecione o banco de dados (esquema) `pokédex`.

```sql
USE pokedex;
```

2. Obtenha informações da estrutura da tabela `Pokémon`.

```sql

```

3. Selecione todos os pokémons cadastrados no banco de dados.

```sql
SELECT * FROM `Pokemon`
```

4. Selecione o `numero`, `nome`, `cor`, `altura_m` e `peso_kg` de todos os pokémons cadastrados.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `cor`, `altura_m`, `peso_kg` FROM `Pokemon`;
```

5. Qual é o `numero` e o `nome` de todos os pokémons da primeira geração?

```sql
USE pokedex; 

SELECT `numero`, `nome` FROM `Pokemon`
WHERE `geracao` = 1;
```

6. Quais são os pokémons `Amarelo` da primeira geração?

```sql
USE pokedex; 

SELECT `nome`, `cor`, `geracao` FROM `Pokemon`
WHERE `cor` = 'amarelo' AND `geracao` = 1;
```

7. Qual é o pokémon mais forte?

```sql
USE pokedex; 

SELECT `nome`, `total` FROM `Pokemon`
ORDER BY `total` DESC
LIMIT 1;
```


8. Selecione o `numero`, `nome` e `tipo1`; de todos os pokémons cujo tipo primário é `Fire`.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `tipo1` FROM `Pokemon`
WHERE `tipo1` = 'Fire';
```

10. Selecione em ordem decrescente o `numero`, `nome` e `defesa` de todos os pokémons.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `defesa` FROM `Pokemon`
ORDER BY `nome` DESC, `defesa` DESC;
```


11. Qual o pokémon possui *menor* taxa de captura? Selecione apenas `numero` e `nome`.

```sql
USE pokedex; 

SELECT `numero`, `nome` FROM `Pokemon`
ORDER BY `taxa_captura` ASC
LIMIT 1;
```


12. Selecione todos pokémons que não possuem tipo secundário, ou seja, `tipo2`.

```sql
USE pokedex; 

SELECT * FROM `Pokemon`
WHERE `tipo2` IS NULL;
```

13. Selecione `numero`, `nome`, `tipo1`, `tipo2` de todos os pokémons que possuem o peso entre 100kg e 500kg.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `tipo1`, `tipo2`, `peso_kg` FROM `Pokemon`
WHERE `peso_kg` >= 100 AND `peso_kg` <= 500;
```


14. Crie um ranking dos top 10 pokémons mais velozes, contendo `numero`, `nome` e `velocidade`.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `velocidade` FROM `Pokemon`
ORDER BY `velocidade` DESC
LIMIT 10;
``` 


15. Selecione `numero`, `nome`, `tipo1`, `tipo2`, `taxa_captura` dos pokémons que possuem os dois tipos e tenham uma taxa de captura acima de 100. Ordene os resultados decrescente pela taxa de captura.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `tipo1`, `tipo2`, `taxa_captura` FROM `Pokemon`
WHERE `taxa_captura` >= 100 
ORDER BY `taxa_captura` DESC;
```

16. Quais são os tipos primários dos pokémons?

```sql
USE pokedex; 

SELECT DISTINCT `tipo1` FROM `Pokemon`;
```

17. Selecione o `numero`, `nome` e `cor`; de todos os pokémons que o nome começa com a letra `D`.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `cor` FROM `Pokemon`
WHERE `nome` LIKE 'd%';
```

18. Qual é o pokémon mais poderoso de todas as gerações?

```sql
USE pokedex; 

SELECT `numero`, `nome`, `total` FROM `Pokemon`
ORDER BY `total` DESC
LIMIT 1;
```

19. Selecione o `numero`, `nome`, `defesa`, `ataque` dos pokémons com defesa > 60 e ataque <= 70; ordenados decrescente pelo `total`. 

```sql
USE pokedex; 

SELECT `numero`, `nome`, `defesa`, `ataque`, `total` FROM `Pokemon`
WHERE `defesa` > 60 AND `ataque` <= 70
ORDER BY `total` DESC;
```

20. Selecione todos os pokémons do tipo `Planta` e `Venenoso` que não sejam `Green`, ordenado crescente pelo `nome`.

```sql
USE pokedex;

SELECT `nome`, `tipo1`, `tipo2`, `cor` FROM `Pokemon`
WHERE `cor` != 'green' AND (
  `tipo1` IN('Planta', 'Venenoso') OR `tipo2` IN('Planta', 'Venenoso'))
ORDER BY `nome` ASC ;
```

21. Selecione de maneira crescente os nomes dos pokémons que possuem a letra y na 4ª posição do nome.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `cor` FROM `Pokemon`
WHERE `nome` LIKE '___y%'
ORDER BY `nome` ASC;
```

22. Qual é o maior valor de `ataque_especial` cadastrado?

```sql
USE pokedex; 

SELECT `numero`, `nome`, `ataque_especial` FROM `Pokemon`
ORDER BY `ataque_especial` DESC
LIMIT 1;
```

23. Selecione o `numero`, `nome` e `altura_m` dos pokémons que possuem altura acima de 2,10m.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `altura_m` FROM `Pokemon`
WHERE `altura_m` > '2,10';
```

24. Quais são as diferentes tipos de cores dos pokémons? Apresente os resultados de maneira crescente pelo nome da cor.

```sql
USE pokedex; 

SELECT DISTINCT `cor` FROM `Pokemon`
ORDER BY `cor` ASC;
```

25. Selecione o `nome` e `velocidade` dos pokémons com velocidade entre 30 e 70. Ordene os resultados por nome (crescente) e velocidade (decrescente)

```sql
USE pokedex; 

SELECT `nome`, `velocidade` FROM `Pokemon`
WHERE `velocidade` > 30 AND  `velocidade` < 70
ORDER BY `nome` ASC, `velocidade` DESC;
```

26. Quem são os pokémons lendários? Apresente os resultados ordenados por `total` decrescente.

```sql
USE pokedex; 

SELECT `nome`, `lendario`, `total` FROM `Pokemon`
WHERE `lendario`
ORDER BY `total` DESC;
```


27. Selecione os pokémons da primeira geração com taxa de captura igual a 255.

```sql
USE pokedex; 

SELECT `nome`, `tipo1`, `taxa_captura` FROM `Pokemon`
WHERE `taxa_captura` = 255;
```


28. Quem é o mais poderoso? selecione o `Pikachu`, `Squirtle`, `Bulbasaur` e `Charmander`; ordenados decrescente pelo `total`. 

```sql
USE pokedex; 

SELECT `nome`, `total` FROM `Pokemon`
WHERE `nome` = 'Pikachu' 
	OR `nome` = 'Bulbasaur' 
	OR `nome` = 'Squirtle'
	OR `nome` = 'Charmander'
ORDER BY `total` DESC;
```

29. Quem são os pokémons da primeira geração, que começam com a letra `d` e não possuem tipo secundário?
Ordene os resultados crescente por `taxa_captura` e decrescente pelo `total`.

```sql
USE pokedex; 

SELECT `nome`, `tipo1`, `total`, `taxa_captura` FROM `Pokemon`
WHERE `tipo1` LIKE 'd%' AND `tipo2` IS NULL
ORDER BY `taxa_captura` ASC, `total` DESC;
```

30. Qual é o ranking dos top 5 pokémons lendários com maior `taxa_captura` e `total`? Apresente apenas `numero, nome, total, taxa_captura` nos resultados.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `lendario`,  `taxa_captura`, `total` FROM `Pokemon`
WHERE `lendario` AND `taxa_captura` AND `total`
ORDER BY `taxa_captura`DESC, `total` DESC
LIMIT 5;
```

31. Selecione o `numero`, `nome`, `peso_kg` dos pokémons com peso entre 2kg e 3kgs?

```sql
USE pokedex; 

SELECT `numero`, `nome`, `peso_kg` FROM `Pokemon`
WHERE `peso_kg` < 2 OR `peso_kg` < 3;
```

32. Selecione o `numero`, `nome`, `tipo1` e `tipo2` dos pokémons com tipo primário `Normal`, que não possuem tipo secundário. Existe algum pokémon lendário nos resultados, se sim, os remova dos resultados?

```sql
USE pokedex; 

SELECT `numero`, `nome`, `tipo1`, `tipo2` FROM `Pokemon`
WHERE `tipo1` = 'normal' AND `tipo2` IS NULL OR `lendario` IS NULL;
```

33. Quem são os pokémons do tipo `Water` que não são azuis? Apresente `numero`, `nome`, `tipo1`, `tipo2` e `cor`, ordenados pelo `nome` de maneira crescente.

```sql
USE pokedex;

SELECT `numero`, `nome`, `tipo1`, `tipo2`, `cor` FROM `Pokemon`
WHERE `cor` != 'Blue' AND (
  `tipo1` IN('Water') OR `tipo2` IN('Water'))
ORDER BY `nome` ASC ;
```

34. Crie um ranking dos top 10 pokémons mais lentos.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `velocidade` FROM `Pokemon`
ORDER BY `velocidade` ASC
LIMIT 10;
```

35. Selecione os pokémons cujo nome comece e termine com a letra `a`. 

```sql
USE pokedex; 

SELECT `nome` FROM `Pokemon`
WHERE `nome` LIKE '%a' AND `nome` LIKE 'a%';
```

36. Quem são os pokémons do tipo `Fire` que não são vermelhos? Apresente `numero`, `nome`, `tipo1`, `tipo2` e `cor`, ordenados pelo `nome` de maneira crescente.

```sql
USE pokedex;

SELECT `numero`, `nome`, `tipo1`, `tipo2`, `cor` FROM `Pokemon`
WHERE `cor` != 'Red' AND (
  `tipo1` IN('Fire') OR `tipo2` IN('Fire'))
ORDER BY `nome` ASC ;
```

37. Quais são os diferentes tipos de `peso_kg` dos pokémons? Apresente os resultados ordenados de maneira crescente.

```sql
USE pokedex; 

SELECT `nome`, `peso_kg` FROM `Pokemon`
ORDER by `peso_kg` ASC;
```

38. Selecione o `numero`, `nome` e `hp` dos pokémons com valores entre 0 e 100. Ordene os resultados de maneira crescente por `hp` e `nome`.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `hp` FROM `Pokemon`
WHERE `hp` > 0 AND `hp` < 100
ORDER by `nome` ASC, `hp` ASC;
```

39. Selecione o `numero`, `nome`, `hp`, `ataque`, `defesa` e `total`; dos pokémons com valores de `hp`, `ataque`, `defesa` maiores ou iguais a 100.

```sql
USE pokedex; 

SELECT `numero`, `nome`, `hp`, `ataque`, `defesa`, `total` FROM `Pokemon`
WHERE `hp` >= 100 AND `ataque` >= 100 AND `defesa` >= 100;
```

40. Selecione todos os pokémons do tipos `Water` e `Gelo`, ordenados decrescente por `total`.

```sql
USE pokedex;

SELECT `nome`, `tipo1`, `tipo2` FROM `Pokemon`
WHERE `tipo1` IN('Water', 'Gelo') OR `tipo2` IN('Water', 'Gelo')
ORDER BY `total` DESC;
```

## 2. Exercícios de Funções Agregadas

1. Quais são os valores máximo e mínimo das seguintes colunas:
    * total
    * hp
    * ataque
    * defesa
    * ataque_especial
    * defesa_especial
    * velocidade
    * taxa_captura

```sql
USE pokedex; 

SELECT
	MAX(`total`) AS `total_max`, 
	MIN(`total`) AS `total_min`
FROM `Pokemon`;

SELECT 
	MAX(`hp`) AS `hp_max`, 
	MIN(`hp`) AS `hp_min`
FROM `Pokemon`;

SELECT 
	MAX(`ataque`) AS `ataque_max`, 
	MIN(`ataque`) AS `ataque_min`
FROM `Pokemon`;

SELECT 
	MAX(`defesa`) AS `defesa_max`, 
	MIN(`defesa`) AS `defesa_min`
FROM `Pokemon`;

SELECT 
	MAX(`ataque_especial`) AS `ataque_especial_max`, 
	MIN(`ataque_especial`) AS `ataque_especial_min`
FROM `Pokemon`;

SELECT 
	MAX(`defesa_especial`) AS `defesa_especial_max`, 
	MIN(`defesa_especial`) AS `defesa_especial_min`
FROM `Pokemon`;

SELECT 
	MAX(`velocidade`) AS `velocidade_max`, 
	MIN(`velocidade`) AS `velocidade_min`
FROM `Pokemon`;

SELECT 
	MAX(`taxa_captura`) AS `taxa_captura_max`, 
	MIN(`taxa_captura`) AS `taxa_captura_min`
FROM `Pokemon`;
```

2. Quantas cores diferentes possuem os pokémons?

```sql
USE pokedex; 

SELECT COUNT(DISTINCT `cor`) FROM `Pokemon`;
```

3. Qual é o peso médio dos pokémons?

```sql
USE pokedex; 

SELECT AVG(`peso_kg`) FROM `Pokemon`;
```

4. Qual é a soma das alturas dos pokémons?

```sql
USE pokedex; 

SELECT SUM(DISTINCT `altura_m`) FROM `Pokemon`;
```

5. Quantos pokémons estão cadastrados no banco de dados?

```sql
USE pokedex; 

SELECT DISTINCT COUNT(`nome`) FROM `Pokemon`;
```

6. Qual é o altura média dos pokémons?

```sql
USE pokedex; 

SELECT AVG( DISTINCT `altura_m`) FROM `Pokemon`;
```

7. Qual é o desvio padrão do valor de HP dos pokémons?
```sql
USE pokedex;

SELECT STD(`hp`) FROM `Pokemon`;
```

8. Quantos pokémons possuem tipo2?

```sql
USE pokedex; 

SELECT DISTINCT COUNT(`tipo2`) FROM `Pokemon`;
```

9. Quantos são os diferentes tipos primários dos pokémons? 

```sql
USE pokedex; 

SELECT DISTINCT COUNT(`tipo1`) FROM `Pokemon`;
```

10. Qual é a soma dos pesos dos pokémons?

```sql
USE pokedex; 

SELECT SUM(DISTINCT `peso_kg`) FROM `Pokemon`;
```

11. Qual é a quantidade de Pokémons lendários e não lendários

```sql
USE pokedex; 

SELECT count(`lendario`) FROM `Pokemon`
WHERE `lendario` = 1;

SELECT count(`lendario`) FROM `Pokemon`
WHERE `lendario` = 0;
```

12. Qual é a quantidade de pokémons para cada uma das diferentes cores ordenadas decrescente?

```sql
USE pokedex; 

SELECT DISTINCT `cor`, COUNT(`cor`) AS `quantidade` FROM `Pokemon`
GROUP BY `cor`
ORDER BY `quantidade` DESC;
```

13. Qual é a média de peso e altura de cada um dos tipos primários dos pokémons? Ordene os resultados decrescente respectivamente por média de peso e altura.
```sql
USE pokedex; 

SELECT DISTINCT `tipo1`, AVG(`peso_kg`) AS `peso`, AVG(`altura_m`) AS `altura` FROM `Pokemon`
GROUP BY `tipo1`
ORDER BY `peso` DESC, `altura` DESC;
```

14. Qual é a taxa de captura média por cor de cada um dos pokémons lendários?

```sql
USE pokedex; 

SELECT `cor`, AVG(`taxa_captura`) AS `taxa_captura`
FROM `Pokemon`
WHERE `lendario` = 1
GROUP BY `cor`;
```

15. Qual os tipos primários que possuem a taxa de captura média acima de 100

```sql
USE pokedex; 

SELECT `tipo1`, `taxa_captura` FROM `Pokemon`
WHERE `taxa_captura` > 100;
```

16. Agrupados por cor, quais pokémons não lendários possuem média total abaixo de 400

```sql
USE pokedex; 

SELECT `cor`, AVG(`total` < 400) AS `total`
FROM `Pokemon`
WHERE `lendario` = 0
GROUP BY `cor`;
```

17. Qual o valor máximo total em cada uma das gerações?

```sql
USE pokedex; 

SELECT `tipo1`, MAX(`total`) AS `total`
FROM `Pokemon`
GROUP BY `tipo1`;


SELECT `tipo2`, MAX(`total`) AS `total`
FROM `Pokemon`
GROUP BY `tipo2`;
```

18. Quantos pokémons lendários existem em cada uma das gerações?

```sql
USE pokedex; 

SELECT count(`tipo1`) AS `tipo1`
FROM `Pokemon`
WHERE `lendario` = 1;


SELECT count(`tipo2`) AS `tipo2`
FROM `Pokemon`
WHERE `lendario` = 1;
```

19. Em cada uma das gerações, quantos pokémons tem tipos primários e secundários e qual a taxa_captura média deles?

```sql
USE pokedex; 

SELECT `tipo1`, `tipo2`, COUNT(`geracao`), AVG(`taxa_captura`) FROM `Pokemon`
GROUP BY `tipo1`, `tipo2`;
```

20. Qual é a quantidade de cores de cada um dos pokémons lendários em todas as gerações?

```sql
USE pokedex; 

SELECT DISTINCT `tipo1`, COUNT(`cor`) AS `cor` FROM `Pokemon`
WHERE `lendario` = 1
GROUP BY `tipo1`
ORDER BY `cor` DESC;

SELECT DISTINCT `tipo2`, COUNT(`cor`) AS `cor` FROM `Pokemon`
WHERE `lendario` = 1
GROUP BY `tipo2`
ORDER BY `cor` DESC;
```


## REFERÊNCIAS

* [Webiste Oficial - Pokémon](https://www.pokemon.com/br/guia-para-pais/)
* [Guia de Estilo SQL · SQL Style Guide](https://www.sqlstyle.guide/pt-br/)







