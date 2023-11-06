# Documentação coffee-etl

## Arquitetura
![image](https://github.com/xmarcelo195/coffee-etl/assets/66145723/3f265f34-8036-40e9-b5e6-14e1303849dd)

## Fonte dos dados 🧭
Api com o histórico da taxa de cambio
  https://docs.openexchangerates.org/reference/api-introduction

Planilha com cotação do preço de café (2019 - 2022)
  Disponibilizada via whatsapp (https://raw.githubusercontent.com/xmarcelo195/coffee-etl/main/src/data/coffee.csv)

## Objetivo
  Consumir uma api e coletar valores de câmbios de 4 moedas (Real - BRL, Euro - EUR e Peso Chileno - CLP) nos últimos 30 dias.

## Tecnologias Utilizadas
  - Python
  - sqlite
  - Google Colab
  - Power BI

## API
### Endpoint utilizado:<br>
  https://docs.openexchangerates.org/reference/historical-json
### Limitações:<br>
  - Necessário buscar 1 data por vez, consulta em lote apenas para premium e cada dia no range é uma requisição
  - Limite de 1000 chamadas por mÊs
### Credencial:<br>
  - No Código
### Suporte disponível <br>
  - Não

## Tabelas
### Cruzamento <br>
  - Base histórica dos preços de Café com o histórico das cotações
  - Key = Coluna de Data.
  
### Formato <br>
  O arquivo que retorna da API é do Tipo Json ele é convertido para pandas dataframe e salvo utilizando sqlite.
  
### POC
  Não houve prova de conceito

### Dicionário Técnico
#### Tabela raw_cambio
  Base de dado crua com o retorno da API de cambios

##### Colunas
  - data (str): data utilizada na chamada do endpoint
  - response (str): json em formato string retornado na chamada do endpoint

#### Tabela curated_cambio
  Tratamento na tabela raw_cambio para extrair os valores do cambio e moeda
##### Colunas
  - data (str): data utilizada na chamada do endpoint
  - moeda (str): Simbolo da moeda (EUR, CLP, BRL)
  - cambio (float): valor do cambio na data para o simbolo

#### Tabela cambios
  Versão completa da curated_cambio que não foi possivel coletar apenas com os dados da API por motivos de limitação de chamados. Colunas exatamente iguais

#### Tabela Coffee
  Dados de cotações de comodity do café entre 01/2019 e 08/2022
##### Colunas
 - Date (str): Data referência
 - Open (float): Valor do preço de abertura na data de referência
 - High (float): Maior Preço atingido na data de referência
 - Low (float): Menor Preço atingido na data de referência
 - Close (float): Preço no fechamento da data de referência
 - Volume (int): Volume de papeis negociados

#### Tabela analytics_coffee
  Identica a tabela coffee porém adiciona linhas referentes aos valores de Open, High,Low,Close convertidos para o Cambio de outras moedas.
