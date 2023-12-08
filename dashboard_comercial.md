# Dashboard Comercial (serviços regulatórios)

## Contextualização
A legislação brasileira estabelece Regras de Prestação do Serviço Público de Distribuição de Energia Elétrica conforme a  [Resolução Normativa ANEEL nº 1.000/2021](https://www2.aneel.gov.br/cedoc/ren20211000.pdf). O artigo 439 da referida resolução diz que a "_qualidade do serviço prestado pela distribuidora será avaliada pela verificação do **cumprimento dos prazos** relacionados no Anexo IV._" Além disso, vale ressaltar que o descumprimento de prazos responsabiliza a distribuidora a creditar uma compensação para o cliente, prejudicando a receita da companhia.

## Cenário
Diante disso, a distribuidora dispõe de um corpo técnico de eletricistas para realização dos serviços solicitados pelos usuários da rede elétrica e dispostos em quatro unidades territoriais de distribuição (**UTD**): Centro, Leste, Oeste e Sul. Cada serviço realizado é mantido sob um documento chamado ordem de serviço (**OSE**), contendo a natureza da atividade, dados do cliente, entre outras informações.

## Identificando o Problema
Nota-se, portanto, que é de suma importância que o setor responsável faça o monitoramento e controle dos prazos de atendimento dos serviços solicitados pelos usuários. Logo, após reuniões e conversas com os _stakeholders_, foi identificada a necessidade de responder aos seguintes questionamentos:
- Qual é o montante total de serviços atendidos?
- Qual é a eficácia global de atendimento? E por UTD?
- Qual tipo de serviço causa mais transgressão de prazo?
- A eficácia aumenta ou diminui ao longo do tempo?

## Preparando os Dados
O maior desafio durante o projeto foi a inexistência de um _Data Warehouse_ que fizesse ETL no CRM da empresa e viabilizasse uma conexão direta com o Power BI. Após uma investigação descobriu-se que a única fonte de dados disponível e confiável eram duas planilhas Excel alimentadas através de um código VBA que exporta e armazena os dados do CRM.

Portanto, foi alinhado com os _stakeholders_ que esta seria a fonte de dados utilizada para a construção das análises.

## Processando os Dados
