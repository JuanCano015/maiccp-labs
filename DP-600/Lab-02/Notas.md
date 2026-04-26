# Lab 02 - Create and use Dataflows (Gen2) in Microsoft Fabric 

## O que o lab propõe
Criar um Dataflow para trasnformar dados e orquestra-lo via pipeline  

## O que eu fiz
Primeiramente loguei na VM criada pelo lab proporcionado pela MAICPP via skillable, criei uma conta no microsoft fabric e criei uma data Lakehouse novamente, para servir de destino para os dados transformados pelo dataflow.

Em seguida criei um dataflow e carreguei os dados por uma URL pública fornecida pelo lab. Durante a configuração desse dataflow eu defini o data gateway como "None" pois a fonte era publica e não exigia intermediário de rede, e o Authentication kind como "Anonymous" pois a URL não exigia credenciais de acesso.

Com os dados carregados, adicionei uma nova coluna chamada "MonthNo" usando como formula "(Date.month([orderDate])" com o tipo de dado como Whole Number. Essa coluna extrai o numero do mes a partir da data do pedido, facilitando análises por periodo.

Antes de salvar validei os tipos de dados "OrderDate" como Date e "MonthNo" como Whole Number e configurei o destino dos dados transformados na minha Lakehouse.
Ápos fazer toda a configuração, criação de coluna para transformação e validação cliquei em 'Save & Run' fazendo o Dataflow ser executado manualmente e aplicando as transformações e salvando os dados no destino configurado

A proxima etapa do lab era criar uma pipeline e para orquestrar o Dataflow automaticamente, porem deu o seguinte erro:

> *Unable to create Pipeline — Creating Pipeline isn't currently supported in this workspace.*

Essa limitação era por conta que a conta trial do fabric não vem com a permissão para criar pipelines por padrão, verifiquei se foi um erro meu de configuração porem o dataflow tinha funcionado corretamente pelo save & run

## Conceitos novos 

### Dataflow Gen 2
O dataflow gen 2 é uma ferramenta de ELT/ETL que permite carregar e limpar dados em larga escala para um destino (no meu caso a minha lakehouse)

### Pipeline
Pipeline é uma ferramenta que permite orquestrar e automatizar fluxos de dados como nesse caso o meu dataflow criado 

## Conexão com o que eu já sabia
O Dataflow fazendo transformação de dados é conceitualmente parecido com uma query SQL selecionar, limpar e estruturar dados. 
A diferença é que o Dataflow tem interface visual, registra cada step automaticamente e já entrega os dados transformados no destino configurado, sem precisar escrever código.
