<h1>Curso Programadores Cariocas</h1>
<h2>Projeto em Grupo Módulo 4 – Resilia</h2>

Grupo: <ol>
              <li>Ana Carolina Aquino</li>
              <li>Gabriela Rosa</li>
              <li>Hebert Garcia</li>
              <li>Lucelde Minô</li>
              <li>Marcelo Gomes</li>
       </ol>

<br><br>
CONTEXTO: <i>Temos um problema e precisaremos da sua ajuda para resolver! Acumulamos alguns conjuntos de dados e não conseguimos ter uma visão padronizada desses dados. O conjunto de dados disponíveis podem ser encontrados aqui:<https://drive.google.com/drive/folders/1F9Rwbzzz4LJCxZU-mTR4JqDT_2vJ7-sC?usp=sharing>.</i><br><br>

<b>⇨ Nesse projeto você e sua squad deverão montar um dashboard com base no conjunto de dados escolhidos por vocês, a fim de realizar uma apresentação com a exploração dos dados.</b><br><br>


A partir dos dados fornecidos optamos por utilizar a tabela GOT_episodes_v4.cvs que apresenta dados sobre os episódios e temporadas da série Game of Thrones.
Durante o Brainstorm sobre perguntas que podem ser respondidas pelos dados selecionamos as seguintes perguntas:<br>

  <ul>
    <li>Quantas temporadas a série possui?</li>
    <li>Quantos episódios a série possui?</li>
    <li>Quantos episódios cada temporada possui?</li>
    <li>Qual o episódio mais bem avaliado de cada temporada?</li>
    <li>Qual o episódio com maior duração?</li>
    <li>Qual o episódio com menor duração?</li>
  </ul>
<br><br>
<b>Abaixo consta uma prévia do dashboard desenvolvido no Power BI.</b><br><br>
       
![img_dashboard_game_of_thrones](https://user-images.githubusercontent.com/113844035/214375329-c4fd1a8b-6931-49b1-b4d2-4348b465f515.png)
  



-------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>Abaixo consta o script de criação do banco de dados .</b>

CREATE DATABASE db_game_of_thrones;<br>
  
USE db_game_of_thrones;<br>
  
CREATE TABLE GOT_episodes (
    id INT NOT NULL AUTO_INCREMENT,
    season INT NOT NULL,
    episode INT NOT NULL,
    title VARCHAR(100) NOT NULL,
    rating DECIMAL(10 , 1) NOT NULL,
    duration INT NOT NULL,
    PRIMARY KEY (id)
);<br><br>

/*Quantas temporadas a série possui?*/
  <br>
SELECT COUNT(DISTINCT season) AS quantidade_de_temporadas FROM got_episodes;
<br><br>
/*Quantos episódios a série possui?*/
  <br>
SELECT COUNT(episode) AS quantidade_de_episódios FROM got_episodes;
<br><br>
/*Quantos episódios cada temporada possui?*/
  <br>
SELECT season, COUNT(episode) AS quantidade_de_episódios_por_temporada FROM got_episodes GROUP BY season;
<br><br>
/*Qual o episódio mais bem avaliado de cada temporada?*/
  <br>
SELECT * FROM got_episodes WHERE  season = 1  ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 2  ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 3  ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 4  ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 5 ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 6 ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 7 ORDER BY rating DESC LIMIT 1;
SELECT * FROM got_episodes WHERE  season = 8 ORDER BY rating DESC LIMIT 1;
<br><br>
/*Qual o episódio com maior duração?*/
  <br>
SELECT season, episode, title, duration FROM got_episodes ORDER BY duration DESC;
<br><br>
/*Qual o episódio com menor duração?*/
  <br>
SELECT season, episode, title, duration FROM got_episodes ORDER BY duration ASC;
