# Nova página no painel — Analytics > Sessões

## Objetivo

Criar uma nova página no painel administrativo do SeuChef para acompanhar os dados de sessões do site vindos do Google Analytics.

A nova página deve permitir visualizar, dentro do painel, a evolução mensal de sessões do site, comparando o ano atual com o ano anterior.

---

## Página sugerida

**Menu:** Marketing > Analytics  
**Página:** `/admin/analytics/sessions`  
**Nome da página:** Analytics — Sessões  
**Arquivo HTML visualização:** `analytics-sessoes.html`  
**Prioridade:** Alta  
**Status:** Pendente  

---

## Problema atual

Hoje o acompanhamento de sessões depende de acessar o Google Analytics fora do painel.

Isso dificulta a leitura operacional dos dados dentro do fluxo do SeuChef, porque as informações de audiência ficam separadas dos demais indicadores do negócio.

---

## Como deve funcionar

Criar uma nova página no painel para exibir os dados de sessões do Google Analytics.

A página deve mostrar um gráfico mensal com:

- Sessões de 2025
- Sessões de 2026
- Comparação mês a mês
- Valores exibidos nos pontos do gráfico
- Filtros por período ou ano, se possível

---

## Integração necessária com Google Analytics

O painel precisa ser integrado ao Google Analytics para buscar os dados reais da conta/propriedade GA4 do SeuChef.

O caminho recomendado é usar a Google Analytics Data API, que permite consultar dados de relatórios do GA4 de forma programática.

A API deve buscar a métrica de sessões, agrupada por mês.

---

## Requisito técnico

Os dados do gráfico não devem ficar fixos no front-end.

O desenvolvedor precisa criar uma integração entre o painel e o Google Analytics para buscar os dados reais da propriedade GA4.

---

## Autenticação

Será necessário configurar acesso à API do Google Analytics.

Etapas técnicas esperadas:

1. Criar ou usar um projeto no Google Cloud.
2. Ativar a Google Analytics Data API.
3. Criar credenciais de acesso.
4. Definir se a integração usará conta de serviço ou OAuth.
5. Dar permissão para a credencial acessar a propriedade do Google Analytics.
6. Informar o Property ID do GA4 no back-end do painel.

Observação: a documentação oficial da Google Analytics Data API permite autenticação com conta de usuário ou conta de serviço. Para painel interno, a conta de serviço costuma ser o caminho mais adequado, desde que tenha permissão na propriedade do GA4.

---

## GET/API — Buscar dados iniciais

Ao carregar a nova página, o front-end deve fazer uma requisição para o back-end do painel.

Exemplo de endpoint interno sugerido:

```txt
GET /api/admin/analytics/sessions
````

Esse endpoint do painel deve consultar o Google Analytics, buscar os dados da propriedade GA4 e retornar as sessões agrupadas por mês.

---

## Envio de filtros

Caso a tela tenha filtros de período, ano ou comparação entre anos, o front-end deve enviar esses filtros para o back-end.

Exemplo:

```txt
GET /api/admin/analytics/sessions?startDate=2025-01-01&endDate=2026-12-31
```

Ou, se o projeto preferir enviar filtros no corpo da requisição:

```txt
POST /api/admin/analytics/sessions/filter
```

Payload sugerido:

```json
{
  "startDate": "2025-01-01",
  "endDate": "2026-12-31",
  "compareYears": [2025, 2026],
  "metric": "sessions"
}
```

---

## Consulta esperada no Google Analytics

A consulta ao Google Analytics deve buscar:

* Métrica: `sessions`
* Dimensão: mês
* Período: ano atual e ano anterior
* Agrupamento: mensal

Exemplo conceitual:

```txt
Métrica: sessions
Dimensão: month
Período: 2025 e 2026
```

---

## Retorno esperado da API interna

O back-end deve retornar os dados já tratados para o gráfico.

Exemplo:

```json
{
  "labels": ["Jan", "Fev", "Mar", "Abr", "Maio", "Jun", "Jul", "Ago", "Set", "Out", "Nov", "Dez"],
  "sessions": {
    "2025": [48000, 47452, 38453, 46697, 38894, 38686, 34072, 26825, 37210, 36648, 33740, 30172],
    "2026": [39235, 36884, 35058, 35435, 39084, null, null, null, null, null, null, null]
  }
}
```

---

## Fluxo esperado

1. Usuário acessa a nova página Analytics > Sessões.
2. Front-end chama o endpoint interno do painel.
3. Back-end consulta a Google Analytics Data API.
4. Google Analytics retorna os dados da propriedade GA4.
5. Back-end trata os dados e organiza por mês.
6. Front-end monta o gráfico com as sessões de 2025 e 2026.
7. Usuário aplica filtros, caso existam.
8. Front-end envia os filtros para a API interna.
9. Back-end refaz a consulta no Google Analytics.
10. Front-end atualiza o gráfico.

---

## Critério de aceite

A melhoria será considerada concluída quando:

* Existir uma nova página no painel para acompanhar sessões do Analytics.
* O painel estiver integrado ao Google Analytics.
* A página exibir gráfico mensal de sessões.
* O gráfico comparar 2025 e 2026.
* Os dados vierem da propriedade GA4 real.
* Os valores não ficarem fixos no front-end.
* Os filtros, se existirem, atualizarem o gráfico.
* Os números exibidos no painel baterem com os dados do Google Analytics.
* A página estiver acessível no menu do painel.

---

## Observações

O nome do endpoint pode ser ajustado conforme a estrutura real do projeto.

O ponto obrigatório é que o painel passe a buscar os dados reais do Google Analytics e reproduza esses dados dentro do painel administrativo.