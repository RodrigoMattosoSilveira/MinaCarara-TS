# MinaCarara-TS
An updated architecture of the POC Mineração Carará project. See Documents for details

# Highlights
We will migrate to an architecture comprise of the following elements:
- **Data**: All data will reside on sheets in the `MinaCarara` spreadsheet;
- **Sheet Access**: It will reside solely on the `WebApp` script; 
- **Logic**: It will reside solely in the `Library`;
- **User Experience**: It will reside solely in the sheets that require it;

# Data
All data will resilde on a single spreadsheet, `MinaCarara`, consisting of the following sheets:
- Pessoa
- Colaborator
- ContasCorrentes
- Método
- Setor
- Área
- Tarefa
- Períodos
- ProduçãoOuro
- CotaçãoOuro
- TabelaPreços

All MinaCarara users will have view access to it, only a few will have edit privileges. All sheets will have 1 header row, frozen; data retrieval logic will select all records starting starting on row 2 and column 1, to lastRow abnd lastColumn-- 1-based;

# Sheet Access
The `WebApp` script will have a `Main` module governing access to all other modules, one per sheet; its main doPost function argument, `e`, will include:
- The module being called - this will keep its case statement small;
- The function with it the module - this will ensure each module will support only its functions;
- The data used by the function;

# Logic
The `Library` will mediate CRUD requests coming from sheets with the `WebApp`, and include modules with common functions used accross the applications, as for instance `dateToString`;

# User Experience
The remaining sheets will iasue UI requests to CRUD data in the `MinaCarara` spreadsheet:

## Despesas 
Spreadsheet with sheets used to capture collaborators expeses on goods and services:
- Cantina
- Diversos
- Pix
- Voo
- Zerar
- Fechar
- Cambio
  
Notes:
- We will explore consolidating all these sheets in one sigle sheet.
- We will maintain the ranges

## Cronograma
Spreadsheet with sheets used to plan and perform the work that yiels production and collaborators' payments:
- Planejar
- Ativos
- Contabilizar
- PDF
- Modelos (better name?)

## ContasCorrente  - we will maintain the ranges
Spreadsheet with sheets used view details of a collaborator's earnings and expenses:
- Colaborador
- CC-Real
- CC-Ouro