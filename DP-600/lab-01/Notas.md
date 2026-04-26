# Lab 01 - Create a Microsoft Fabric Lakehouse 

## O que o lab propõe
Crie uma Lakehouse usando o microsoft Fabric

## O que eu fiz
Primeiramente loguei na VM criada pelo lab proporcionado pela MAICPP, criei uma conta no microsoft fabric, aprendi um pouco sobre a interface do programa e logo após criei uma data Lakehouse.

Dentro a workspace da minha Lakehouse baixei um csv de vendas tambem proporcionado pelo lab e carreguei minha Lakehouse com.
Após carregar minha Lakehouse transformei os dados do csv em tabela para que eu pudesse realizer consultas via queries SQL.

Explorei tambem as opções de shortcut para os meus dados tendo em vista que em algumas ocasiões pode ocorrer de ter muitos dados para trabalhar e fazendo um shortcut eu poderia agilizar um processo redundante de ter que localizar os dados toda vez que eu fosse trabalhar com ele.

Realizei tambem uma consulta SQL usando a ferramenta visual do Microsoft Fabric, usando a interface arrasta e solta e selecionando as tabelas para a consulta por checkboxes.


## Novos conceitos aprendidos
## Delta table
É uma camada sobre o parquet que atua como uma auditoria automatica.
Cada operação feita fica registrada no _delta_log permitindo rastrear o que mudou, quando mudou e quem mudou possibilitando tambem desfazer as mudanças feitas. 

## Parquet
É um formato de armazenamento de arquivos formatados por colunas projetado para performance, ao inves de ler todas a colunas assim como um csv ele foca apenas em ler oque é consultado

## Querie da consulta realizada

SELECT Items, SUM(quantity * UnitPrice) as Revenue
FROM sales
GROUP BY Item
ORDER BY Revenue DESC;

## Conexão com o que eu já sabia
O conceito do "_delta_log" é parecido com auditoria de dados que eu já havia implementado manualmente em SQL a ideia é a mesma: registrar cada operação feita nos dados para permitir rastreabilidade.
A diferença é que o Delta Lake faz isso nativamente na camada de armazenamento, sem precisar de nenhuma lógica adicional.
