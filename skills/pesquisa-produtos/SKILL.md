---
name: pesquisa-produtos
description: Pesquisar produtos em um site de vendas e gerar um resumo estruturado em Markdown sem inventar resultados.
---

# Pesquisa de produtos

## Objetivo

Pesquisar produtos em um site de vendas e gerar um resumo em Markdown com os dados encontrados de forma verificável.

## Entradas

- `site`: URL base do site de vendas.
- `termos de busca`: um ou mais nomes, palavras-chave ou descrições dos produtos procurados.
- `filtros` (opcionais): categoria, faixa de preço, disponibilidade, avaliação, ordenação ou outros filtros oferecidos pelo site.
- `quantidade de resultados`: número máximo de itens a registrar por termo.
- `limite de páginas` (opcional): número máximo de páginas do catálogo a percorrer; usar um limite seguro e informado pelo usuário.

## Passo a passo

1. Abrir o `site` informado e confirmar que o catálogo ou a página de produtos foi carregada.
2. Para cada termo de busca:
   1. Procurar um campo de busca.
   2. Se houver campo de busca, preencher o termo, executar a pesquisa e examinar os resultados.
   3. Aplicar os filtros opcionais somente quando forem compatíveis com o que o site oferece.
   4. Se não houver campo de busca ou o termo não produzir correspondências, identificar a categoria mais provável relacionada ao produto e navegar por ela.
   5. Se ainda não houver correspondências, percorrer a paginação do catálogo **até o limite máximo de páginas** indicado nas entradas.
   6. Parar assim que o limite for atingido, o catálogo terminar ou forem encontrados a quantidade solicitada de resultados relevantes.
3. Para cada produto encontrado, verificar e registrar apenas dados presentes na página:
   - Título;
   - Preço;
   - Disponibilidade;
   - Avaliação, como estrelas ou pontuação exibida;
   - Categoria;
   - Link do produto, quando disponível.
4. Para o primeiro resultado relevante de cada termo, abrir a página do produto e obter um resumo de 2 ou 3 linhas da descrição. Traduzir o resumo para português apenas quando necessário.
5. Se nenhum produto correspondente for encontrado para um termo, registrar exatamente `não encontrado` e listar os locais ou etapas pesquisados.
6. Reunir os resultados em Markdown e salvar no arquivo solicitado.

## Estratégia de busca

A ordem obrigatória é:

1. **Campo de busca** → pesquisar diretamente o termo.
2. **Categoria provável** → navegar pela categoria mais adequada ao produto, como categoria, departamento ou coleção equivalente.
3. **Paginação limitada** → percorrer no máximo o limite informado de páginas do catálogo e então parar.

Não continuar além do limite de páginas. Não substituir uma busca não realizada por suposições sobre o catálogo.

## Regras

- Nunca inventar títulos, preços, disponibilidade, avaliações, categorias, descrições, links ou resultados.
- Registrar somente dados que possam ser confirmados no site consultado.
- Usar correspondências pertinentes ao termo; não considerar títulos apenas remotamente relacionados como resultado sem evidência.
- Respeitar o limite de páginas e a quantidade máxima de resultados por termo.
- Não registrar dados pessoais de vendedores, compradores ou operadores do site, como nomes, contatos, endereços, telefones ou documentos.
- Não incluir credenciais, cookies ou informações privadas coletadas durante a navegação.
- Se a página não divulgar algum campo, registrar `não informado` em vez de deduzir o valor.
- Distinguir claramente entre resultados encontrados e termos não encontrados.
- Mencionar a URL consultada e registrar brevemente onde cada termo foi procurado.

## Formato do arquivo de saída

O arquivo deve ser um Markdown chamado `resultado-busca.md`, salvo na raiz do workspace, salvo indicação contrária do usuário.

Usar a estrutura abaixo:

```markdown
# Resultado da busca

Fonte: <URL ou nome do site>

## <Termo pesquisado>

### Resultados

#### <Título do produto 1>

- Preço: <preço confirmado ou não informado>
- Disponibilidade: <informação confirmada ou não informado>
- Avaliação: <avaliação confirmada ou não informado>
- Categoria: <categoria confirmada ou não informado>
- Link: <URL confirmada ou não informado>

Resumo da descrição do primeiro resultado:
<Resumo fiel de 2 ou 3 linhas em português, quando disponível>

#### <Título do produto 2>

- Preço: <preço confirmado ou não informado>
- Disponibilidade: <informação confirmada ou não informado>
- Avaliação: <avaliação confirmada ou não informado>
- Categoria: <categoria confirmada ou não informado>
- Link: <URL confirmada ou não informado>

Se não houver resultados:

**não encontrado**

Locais pesquisados:
- Campo de busca: <resultado ou indisponível>
- Categoria: <categoria consultada ou não aplicável>
- Paginação: <quantidade real de páginas percorridas>

## Observações

- Limite de resultados por termo: <quantidade>
- Limite de páginas: <quantidade>
- Dados indisponíveis foram registrados como `não informado`.
```
