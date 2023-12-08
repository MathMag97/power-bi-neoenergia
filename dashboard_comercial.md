# Dashboard Comercial (serviços regulados) 80%

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

Também foi necessária a criação de uma tabela dimensão chamada [dim_comercial] para categorizar os serviços e simplificar a análise.

Portanto, foi alinhado com os _stakeholders_ que estes seriam o conjunto de dados utilizado para a construção das análises.

<img src="/assets/servicos-regulados/dados_resolução_1000.png" alt="Conjunto de dados"/>

## Processando os Dados
Foi utilizada os recursos do Power Query e da Linguagem M para importar e processar os dados.
<details>
  <summary>Mostrar imagens</summary>
  Código em M:
  
  <img src="/assets/servicos-regulados/M_code.png" alt="Código em M"/>

  Dados no Power Query e as etapas aplicadas:
  
  <img src="/assets/servicos-regulados/PQ_import.png" alt="Power Query"/>

  Modelo de dados:
  
  <img src="/assets/servicos-regulados/model.png" alt="Data Model"/>
  
</details>

## Analisando os dados
Só foi construída uma medida em DAX para encontrar o número total de serviços:

```Total Serviços = DISTINCTCOUNT('f_OSE'[OS])```

Os demais filtros foram realizados através das próprios campos contidos no conjunto de dados ou incluídos no mesmo (PQ).

<details>
  <summary>Mostrar relatório</summary>
  
  <img src="/assets/servicos-regulados/dash_comercial_regulados.png" alt="Dashboard Comercial - Serviços Regulados" style="height: 1200px, width: 1280px" />
  
</details>

## Compartilhando os dados

Em breve.

## Plano de ação

Em breve.
