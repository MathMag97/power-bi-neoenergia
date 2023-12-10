# Comercial - Serviços Regulados (80%)

Os _stakeholders_ tinham dificuldade em acompanhar a qualidade dos serviços prestados pela distribuidora quanto ao cumprimento de prazos. Nesse sentido, realizei o ETL com o CRM da empresa, analisei os dados e construí um Dashboard (_data viz)_ com atualizações em tempo real. Portanto, através de metas e planos de ações, as trangressões de prazos foram reduzidas em 53,39% no 2° trimestre com relação ao 1° trimestre.

<details>
  <summary> Mostrar Dashboard (spoiler) </summary>
  
  <img src="/assets/servicos-regulados/dash_comercial_regulados.png" alt="Dashboard Comercial - Serviços Regulados" style="height: 1200px, width: 1280px" />
  
</details>

## Contexto
A legislação brasileira estabelece Regras de Prestação do Serviço Público de Distribuição de Energia Elétrica conforme a  [Resolução Normativa ANEEL nº 1.000/2021](https://www2.aneel.gov.br/cedoc/ren20211000.pdf). O artigo 439 da referida resolução diz que a "_qualidade do serviço prestado pela distribuidora será avaliada pela verificação do **cumprimento dos prazos** relacionados no Anexo IV._" Além disso, vale ressaltar que o descumprimento de prazos responsabiliza a distribuidora a creditar uma compensação para o cliente, prejudicando a receita da companhia.

## Cenário
Diante disso, a distribuidora dispõe de um corpo técnico de eletricistas para realização dos serviços solicitados pelos usuários da rede elétrica e dispostos em quatro unidades territoriais de distribuição (**UTD**): Centro, Leste, Oeste e Sul. Cada serviço realizado é mantido sob um documento chamado ordem de serviço (**OSE**), contendo a natureza da atividade, dados do cliente, entre outras informações.

## 1. Identificação do Problema
Após reuniões e conversas com os _stakeholders_, foi identificada a necessidade de responder às seguintes perguntas:
- Qual é o montante total de serviços atendidos?
- Qual é a eficácia global de atendimento? E por UTD?
- Qual tipo de serviço causa mais transgressão de prazo?
- A eficácia aumenta ou diminui ao longo do tempo?

## 2. Preparação dos Dados
  - Premissas:
    - Dados diários
    - Datas de abertura, prazo e conclusão do serviços
    - Dados nominais contendo região e categoria de serviço
    - Dados booleanos de status (prazo e fora prazo)
  - Restrições:
    - Inexiste um _Data Warehouse_ na empresa
    - Não há acesso ao banco de dados do CRM, via SQL ou exportação .csv, etc
  
  Após conversa com especialistas no setor, descobrimos que um funcionário de outro departamento exportava através de um código VBA os dados do CRM e os armazenavam em planilhas Excel. Estes dados foram **coletados**, **armazenados** e **importados** no Power Query e, após análise, verificamos que o conjunto de dados atendia às premissas. Nesta etapa, foram verificados os _data types_ e a estrutura geral dos dados.

> Foi necessária a criação de uma tabela dimensão chamada [d_comercial] e uma calendário [calendar] para categorizar os serviços e simplificar os filtros durante a análise.

Portanto, foi alinhado com os _stakeholders_ que utilizaríamos este conjunto de dados para a construção das análises.

<img src="/assets/servicos-regulados/dados_resolução_1000.png" alt="Conjunto de dados"/>

## Processando os Dados
Foi utilizado os recursos do Power Query e da Linguagem M para importar e processar (limpar e transformar) os dados.
<details>
  <summary>Mostrar imagens</summary>
  
  ### Código em M:
  
  <img src="/assets/servicos-regulados/M_code.png" alt="Código em M"/>

  ### Dados no Power Query e as etapas aplicadas:
  
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
