# E-o-Oscar-vai-para...-
Atividade do banco de dados do Oscar, usando o MYSQL.

Hoje vamos trabalhar com o Oscar. A ideia de premiar ou ser premiado é para reconhecer:
- Reconhecer uma qualidade
- Reconhecer um atributo
- Reconhecer o esforço... 

Reconhecer sempre.

Nem todos os prêmios são merecidos e nem todos que merecem ganham. 
Então vale mesmo a pena, premiar? 
##

1- Quantas vezes Natalie Portman foi indicada ao Oscar?

R: 6 vezes;
SELECT COUNT(*) FROM oscar WHERE name = "Natalie Portman"
##
2- Quantos Oscars Natalie Portman ganhou?

R: 2 oscars;
SELECT COUNT(*) FROM oscar WHERE name = "Natalie Portman" AND winner = "True"
##
3-Amy Adams já ganhou algum Oscar?

R: Não;
SELECT COUNT(*) FROM oscar WHERE name = "Amy Adams" AND winner = "True"
##
4- Alguém já ganhou um Oscar e tem o seu primeiro nome?

R: Não;
SELECT * FROM `oscar` WHERE name LIKE '%Thiago%' and winner = 'True'
##
5- Toy Story 3 ganhou um Oscar em quais anos?

R: 2010;
SELECT * FROM `oscar` WHERE film LIKE '%Toy Story 3%' AND winner = 'True'
##
6- Quem tem mais Oscars: a categoria "Melhor Ator" ou "Melhor Filme"?

R: A categoria 'Melhor ator', incluindo 'Lead role' e 'supporting role' tem 872 oscars; já 'Melhor filme' tem 333 oscars;

SELECT COUNT(*) FROM `oscar` WHERE category LIKE '%ACTOR%';

SELECT COUNT(*) FROM `oscar` WHERE category LIKE '%BEST PICTURE%'
##
7- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?

R:  Janet Gaynor, a cerimonia foi no ano de 1928, pelo filme: 	
7th Heaven;
SELECT * FROM oscar WHERE category LIKE '%ACTRESS%' AND winner = 'True'
##
8- Na categoria Winner, altere todos os valores com "True" para 1 e todos os valores "False" para 0.

R: UPDATE oscar SET winner = "1" WHERE winner = "True";
UPDATE oscar SET winner = "0" WHERE winner = "False";
##
9- Em qual edição do Oscar "Crash" ganhou o prêmio?

R: No ano de 2006 e na cerimonia 78;
SELECT * FROM `oscar` WHERE film = 'Crash' AND winner = '1'
##
10- Que filme merecia ganhar um Oscar e não ganhou?

R: BlacKkKlansman / Infiltrado na Klan devia ter ganhado na cerimônia de 2019. Foi criminoso o Green Book ganhar;

SELECT * FROM `oscar` WHERE year_ceremony = '2019' and category = 'BEST PICTURE';
##
11- Bom... dê um Oscar para esse filme, então.

R: Pronto, a justiça foi feita;

UPDATE oscar SET winner = "1" WHERE film = 'BlacKkKlansman' AND category ='BEST PICTURE';

UPDATE oscar SET winner = "0" WHERE film = 'Green Book' AND category ='BEST PICTURE'
##
12- O filme Central do Brasil aparece no Oscar?

R: Sim, aparece com o nome em inglês;
SELECT * FROM `oscar` WHERE film = 'Central Station'
##
13- Aliás... Qual sua opinião sobre central do Brasil

R: Ainda não vi, então não posso opinar;
##
14- Inclua no banco 7 filmes que nunca nem foram nomeados ao Oscar, mas que na sua opinião, merecem.

R: Filmes: Ghost in the shell - O Fantasma do futuro -1995, Expresso do Amanhã - Snowpiercer - 2013, bacurau - 2019, waves - 2019, As vantagens de ser invisível - 2012,
Evangelion: 1.0 You Are (Not) Alone - 2007, Pacific Rim - 2013 e John Wick 2 - 2012;

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (1995,1996,68,"ANIMATED FEATURE FILM","Mamoru Oshii","Ghost in the Shell - O Fantasma do futuro","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2013,2014,86,"BEST PICTURE","Jeong Tae-sung, Steven Nam, Park Chan-wook, Lee Tae-hun, Bong Joon-ho","Expresso do Amanhã - SNOWPIERCER","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2019,2020,92,"FOREIGN LANGUAGE FILM","Brazil","Bacurau","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2019,2020,92,"CINEMATOGRAPHY","Drew Daniels","Waves","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2012,2013,85,"WRITING (Adapted Screenplay)","Screenplay by Stephen Chbosky","As vantagens de ser invisível","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2007,2008,80,"ANIMATED FEATURE FILM","Hideaki Anno","Evangelion: 1.0 You Are (Not) Alon","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2013,2014,86,"VISUAL EFFECTS","Hal T. Hickel, John Knoll, Lindy DeQuattro, Nigel Sumner","Pacific Rim","1");

INSERT INTO oscar (`year_film`, `year_ceremony`, `ceremony`,`category`,`name`,`film`, `winner`) VALUES (2017,2018,90,"FILM EDITING","Evan Schiff","John Wick 2","1");
##
15- Crie uma nova categoria de premiação. Qualquer prêmio que você queira dar. Agora vamos dar esses prêmios aos filmes que você cadastrou na questão acima.

R: Categoria "BEST VIBES", é o premio do filme cujas vibes foram um dos maiores, ou, destaque maior do mesmo;

UPDATE `oscar` SET `category`="BEST VIBES" WHERE film = 'Ghost in the shell - O Fantasma do futuro';

UPDATE `oscar` SET `category`="BEST VIBES" WHERE film = 'Expresso do Amanhã - SNOWPIERCER';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'Bacurau';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'Waves - Ondas';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'The perks of being a wallflower - As vantagens de ser invisivel';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'Evangelion: 1.0 You Are (Not) Alone';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'Pacific Rim - Círculo de Fogo';

UPDATE `oscar` SET `category`= "BEST VIBES" WHERE film = 'John Wick Chapter 2 - Um novo dia para matar';
##
16- Qual foi o primeiro ano a ter um prêmio do Oscar?

R: 1928 foi o ano da primeira cerimônia do Oscar

SELECT * FROM `oscar` WHERE ceremony = '1'
##
17- Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?

R: No ano de 2000, o mesmo de meu nascimento, foram premiados:

Como melhor filme: Bruce Cohen and Dan Jinks, Producers pelo filme American Beauty;
Melhor diretor: Sam mendes pelo filme American Beauty;

Melhor atriz em papel principal: Hilary Swank pelo filme Boys don’t Cry;

SELECT * FROM `oscar` WHERE year_ceremony = 2000 AND winner = '1'
##
18- Agora procure 7 atrizes que não sejam americanas, europeias ou brasileiras.  Vamos cadastrá-los no nosso banco, mas eles ainda não ganharam o Oscar. Só foram nomeados.

R: So-dam Park (Coreana) - Parasita, Yû Aoi (Japonesa)- Samurai X 1 : O Filme, Maggie Cheung (Chinesa)- In the mood for love - Amor à Flor da Pele,

Meng'er Zhang (Chinesa)- Shang-Chi and the Legend of the Ten Rings Shang-Chi e a Lenda dos Dez Anéis,

Ming-Na Wen (Chinesa)- Chun Li- Street Fighter - Street Fighter: A Última Batalha, Cate Blanchett  (Australiana) -Thor Ragnarok - 2017,

Margot Robbie (Australiana) - The Suicide Squad - O esquadrão Suicida;

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2019,2020,92,"ACTRESS IN A SUPPORTING ROLE","So-dam Park","Parasite - Parasita","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2012,2013,85,"ACTRESS IN A SUPPORTING ROLE","Yû Aoi","Rurouni Kenshin: Part I - Origins - Samurai X 1: O Filme","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2000,2001,73,"ACTRESS IN A LEADING ROLE","Maggie Cheung","In the mood for love - Amor à Flor da Pele","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2021,2022,94,"ACTRESS IN A SUPPORTING ROLE","Meng'er Zhang","Shang-Chi and the Legend of the Ten Rings - Shang-Chi e a Lenda dos Dez Anéis","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (1994,1995,67,"ACTRESS IN A SUPPORTING ROLE","Ming-Na Wen","Street Fighter - Street Fighter: A Última Batalha","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2017,2018,90,"ACTRESS IN A SUPPORTING ROLE","Cate Blanchett","Thor: Ragnarok","0");

INSERT INTO `oscar`(`year_film`, `year_ceremony`, `ceremony`, `category`, `name`, `film`, `winner`) VALUES (2021,2022,94,"ACTRESS IN A SUPPORTING ROLE","Margot Robbie","The Suicide Squad - O esquadrão Suicida","0");
##
19- [OPCIONAL] - Utilizando o comando 'Alter Table', troque os tipos dos dados da coluna/campo "Winner" para Bit.

R:ALTER TABLE oscar CHANGE winner bit INT(10)
##
