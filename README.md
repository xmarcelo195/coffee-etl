# Documentação coffee-etl

## Fonte dos dados 🧭
Api com o histórico da taxa de cambio
  https://docs.openexchangerates.org/reference/api-introduction

Planilha com cotação do preço de café (2019 - 2023)
  Disponibilizada via whatsapp (colocar link)

## Objetivo
  Consumir uma api e coletar valores de câmbios de 4 moedas (Real - BRL, Euro - EUR e Peso Chileno - CLP) nos últimos 30 dias.

## Tecnologias Utilizadas
  - Python
  - sqlite
  - Google Colab
  - Power BI

## API
Endpoint utilizado:
  https://docs.openexchangerates.org/reference/historical-json
Limitações:
  - Necessário buscar 1 data por vez, consulta em lote apenas para premium e cada dia no range é uma requisição
  - Limite de 1000 chamadas por mÊs
Credencial:
  - No Código
Suporte disponível
  - Não

Cruzamento 🔀
  - Base histórica dos preços de Café com o histórico das cotações
  - Key = Coluna de Data.
  
Formato
  O arquivo que retorna da API é do Tipo Json ele é convertido para pandas dataframe e salvo utilizando sqlite.
  
POC
  Não houve prova de conceito

<fazer depois>
Dicionário Técnico
Nome da coluna
Tipo do dado
Observação (descrição do dado)
Dicionário Cliente 📖
Schema do DB
Nome da Tabela
Coluna/Campo
Origem/Sistema



O que esse campo/coluna significa?
Contrato de Dados 📶🫱🏾‍🫲🏼
Lista de colunas
Requisição de formatos das colunas
Schema(s)
Fonte(s)
Descrições das informações requeridas
Incrementação ou atualização
