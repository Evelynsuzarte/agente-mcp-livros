# Registro de prompts

## Contexto da tarefa

Teste da skill `pesquisa-produtos` em um site de vendas, com busca do termo **Jeans** e aplicação de filtro de categoria ou marca.

## Prompts utilizados

### Prompt 1

> preiiso que voce teste a skill em um site: https://automationexercise.com/ e pesquise um produto como "Jeans" e aplique um filtro de categoria ou marca

**Resultado:** abertura do catálogo, busca por “Jeans” e aplicação do filtro de categoria `Men > Jeans`.

### Prompt 2

> nao apague o reusltado anterior, registre adicionado

**Resultado:** preservação dos resultados anteriores do Books to Scrape e adição dos resultados do Automation Exercise em `resultado-busca.md`.

### Prompt 3

> Registro de prompts:crie um `PROMPTS.md` com os prompts usados, uma coisa que o agente fez de errado ou diferente do esperado e o consumo aproximado de tokens.

**Resultado:** criação deste registro.

## Erro ou desvio observado

Durante a navegação automatizada, os controles do campo de busca não foram encontrados imediatamente por meio de seletores ou referências antigas da página. Também houve uma tentativa incorreta ao informar uma referência de elemento que já não existia no snapshot atual. O problema foi contornado preenchendo o campo por meio de um script Playwright e submetendo a busca pelo botão correspondente.

Além disso, a skill original exigia registrar apenas dados exibidos. Como a página não mostrava avaliação para os produtos e não exibia uma descrição textual, esses campos foram registrados como `não informado`, sem inventar informações.

## Consumo aproximado de tokens

- Prompt do usuário e contexto das primeiras etapas: aproximadamente 1.500 tokens.
- Navegação, leitura de snapshots e coleta dos dados: aproximadamente 6.000 a 8.000 tokens.
- Atualizações dos arquivos Markdown: aproximadamente 1.500 a 2.500 tokens.
- Respostas e confirmações: aproximadamente 300 a 500 tokens.

**Estimativa total aproximada:** 9.300 a 12.500 tokens.

> O consumo exato não é exposto nesta sessão; este valor é uma estimativa baseada no volume de texto processado e nas chamadas realizadas.
