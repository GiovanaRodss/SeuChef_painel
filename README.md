# Melhorias Necessárias — Painel SeuChef

Este projeto reúne as melhorias, ajustes e novas funcionalidades que precisam ser implementadas no painel administrativo do SeuChef.

O objetivo é documentar de forma visual e organizada o que precisa ser alterado no painel, facilitando o entendimento do desenvolvedor responsável pelo projeto.

---

## Objetivo do projeto

Centralizar as solicitações de melhoria do painel administrativo do SeuChef, incluindo:

- Correções de cálculos financeiros
- Novos gráficos gerenciais
- Melhorias nas páginas operacionais
- Integrações com ferramentas externas
- Ajustes de visualização de dados
- Regras técnicas para buscar dados reais da base

---

## Estrutura dos arquivos

Os arquivos deste projeto foram criados principalmente em HTML para permitir a visualização das melhorias no navegador.

Cada arquivo HTML funciona como uma página de referência visual, contendo:

- Descrição da melhoria
- Problema atual
- Como deve funcionar
- Critérios de aceite
- Requisitos técnicos
- Exemplo visual do gráfico ou tela sugerida

---

## Páginas de melhoria documentadas

### Financeiro > Venda

Arquivo:

```txt
vendas-grafico.html
````

Melhorias propostas:

* Corrigir cálculo da receita geral
* Incluir assinaturas na Receita Bruta e Receita Líquida
* Substituir gráfico de evolução por gráfico comparativo de meta, realizado e alcance

---

### Operacional > Candidato

Arquivo:

```txt
candidatos-grafico.html
```

Melhoria proposta:

* Adicionar gráfico mensal de cadastros de candidatos

---

### Operacional > Empresa

Arquivo:

```txt
empresas-grafico.html
```

Melhoria proposta:

* Adicionar gráfico mensal de cadastros de empresas/estabelecimentos

---

### Operacional > Vaga

Arquivo:

```txt
vagas-grafico.html
```

Melhorias propostas:

* Adicionar gráfico de vagas por tipo
* Adicionar gráfico comparativo de vagas publicadas por ano
* Comparar dados de 2025 e 2026

---

### Operacional > Candidatura

Arquivo:

```txt
candidaturas-grafico.html
```

Melhoria proposta:

* Adicionar gráfico de candidaturas, vagas publicadas e média de candidatos por vaga

---

### Analytics > Sessões

Arquivos:

```txt
analytics-sessoes.html
analytics-sessoes.md
```

Melhoria proposta:

* Criar uma nova página no painel para acompanhar sessões do site
* Integrar o painel com o Google Analytics
* Buscar dados reais do GA4
* Exibir gráfico comparativo de sessões entre 2025 e 2026

---

## Requisito técnico importante

Os dados usados nos gráficos HTML são apenas exemplos visuais.

Na implementação final do painel, os valores não devem ficar fixos no front-end.

O desenvolvedor precisa:

1. Buscar os dados reais da base de dados do painel.
2. Criar ou utilizar endpoints de API.
3. Fazer requisições GET para carregar os dados iniciais.
4. Enviar filtros aplicados na tela para recalcular os dados.
5. Atualizar os gráficos dinamicamente com os dados retornados.
6. Garantir que os números exibidos no painel batam com a base real.

---

## Integração com Google Analytics

Para a página de Analytics, será necessário integrar o painel com o Google Analytics, preferencialmente usando a Google Analytics Data API.

Essa integração deve permitir buscar métricas como:

* Sessões
* Usuários
* Períodos por mês
* Comparação entre anos

Os dados devem vir da propriedade GA4 real do SeuChef.

---

## Como visualizar os arquivos HTML

Para visualizar as páginas no navegador usando o VSCode:

1. Abra o projeto no VSCode.
2. Instale a extensão **Live Server**, caso ainda não tenha.
3. Clique com o botão direito em um arquivo `.html`.
4. Selecione **Open with Live Server**.

Exemplo:

```txt
vagas-grafico.html
```

---

## Status geral

Este projeto é uma documentação visual e funcional das melhorias necessárias.

Status atual:

```txt
Em levantamento e organização das melhorias
```

---

## Observação

Este repositório não representa a versão final do painel em produção.

Ele serve como material de apoio para apresentar, aprovar e orientar a implementação das melhorias no painel administrativo do SeuChef.
