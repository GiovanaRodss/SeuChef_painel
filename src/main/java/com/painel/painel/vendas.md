## Financeiro > Venda

### Correção da Receita Geral: Receita Bruta e Receita Líquida

**Prioridade:** Alta
**Status:** Pendente
**Área:** Financeiro
**Página:** `/admin/sales`
**Menu:** Financeiro > Venda

---

### Problema atual

Na página **Financeiro > Venda**, os valores de **Receita Bruta** e **Receita Líquida** estão incorretos.

Atualmente, o painel considera apenas as vendas de vagas avulsas e pacotes, mas **não inclui os valores das assinaturas compradas no mês**.

Com isso, a receita geral exibida no painel fica menor do que a receita real recebida pelo SeuChef.

---

### Como deve funcionar

A receita geral da página deve considerar todas as transações pagas no período, incluindo:

* Vagas avulsas
* Pacotes de vagas
* Assinaturas

---

### Ajuste necessário

Adicionar as vendas de **assinaturas pagas** no cálculo da receita geral da página.

A **Receita Bruta** deve considerar o valor total pago pelo cliente:

```txt
Receita Bruta = Vendas avulsas + Pacotes + Assinaturas pagas
```

A **Receita Líquida** deve considerar o valor recebido após taxas:

```txt
Receita Líquida = Receita Bruta - Taxas de pagamento
```

As assinaturas também precisam entrar no cálculo líquido, descontando corretamente as taxas aplicadas pelo meio de pagamento.

---

### Critério de aceite

A melhoria será considerada concluída quando:

* As assinaturas pagas entrarem no cálculo da Receita Bruta.
* As assinaturas pagas entrarem no cálculo da Receita Líquida.
* As taxas das assinaturas forem descontadas corretamente na Receita Líquida.
* O valor geral da receita bater com o total real de transações pagas no período.
* O cálculo funcionar para o mês atual e também para filtros de período.
* Os cards de **Últimos 30 dias** e **Últimos 90 dias** também considerarem as assinaturas, caso usem a mesma lógica de receita geral.

---

### Observação

Verificar se os indicadores abaixo também estão ignorando assinaturas:

* Últimos 30 dias
* Últimos 90 dias
* Empresas pagantes
* Transações
* Ticket médio
* Gráfico de receita por mês

Caso estejam, corrigir todos para considerar a receita completa do SeuChef.
