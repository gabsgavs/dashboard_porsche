# 🏎️ Dashboard Analítica de Vendas Porsche

Este repositório contém o código-fonte e a documentação de uma dashboard interativa desenvolvida em um arquivo único (HTML/JS/CSS) para analisar 100 registros de vendas de veículos da Porsche. O projeto faz parte de um estudo prático de Business Intelligence, focando na extração de insights estratégicos e na publicação rápida de aplicações web estáticas.

---

## 📌 1. Perguntas de Negócio Escolhidas e Justificativa

Em vez de acumular gráficos sem propósito, a dashboard foi desenhada para responder a três perguntas estratégicas:

1. **Concentração Geográfica (Faturamento por Estado):** 
   * *Por quê?* Identificar os estados com maior faturamento orienta onde concentrar esforços de marketing, eventos e relacionamento com clientes premium.
2. **Mix de Produtos (Receita por Modelo):** 
   * *Por quê?* Separa "volume de vendas" de "impacto no faturamento", mostrando quais modelos realmente sustentam a receita da marca, ajudando na gestão de portfólio.
3. **Liquidez e Comportamento de Compra (Métodos de Pagamento):** 
   * *Por quê?* Revela a preferência financeira dos compradores (ex: financiamento, pagamento à vista, transferência bancária), o que impacta diretamente a previsibilidade de caixa.

---

## 🤖 2. Ferramenta e Processo (A "Mágica" do Canvas)

Para este projeto, foi utilizado o **Gemini com Canvas**. O diferencial do processo foi delegar à inteligência artificial tanto a estruturação visual quanto o tratamento dos dados, enviando a base bruta diretamente para o agente.

O fluxo funcionou da seguinte maneira:
1. A planilha original com os dados brutos de 100 vendas (com datas em formatos variados e nomenclaturas de colunas irregulares) foi fornecida diretamente no chat, **sem tratamento prévio manual no Excel**.
2. O prompt instruiu a IA a estruturar o HTML e garantir a leitura correta dos campos necessários para os cálculos.
3. A própria IA estruturou o array de dados dentro do JavaScript do arquivo `index.html`, criando variáveis sanitizadas no código para as datas, valores numéricos de preço e agrupamentos de modelos, para que os filtros funcionassem perfeitamente na interface final.

---

## 📝 3. O Prompt Utilizado

Abaixo está o prompt exato que foi submetido à IA, junto com o arquivo da planilha, e que gerou o arquivo HTML funcional na primeira tentativa, sem necessidade de refinamento adicional:

> Você é um desenvolvedor front-end sênior e especialista em Business Intelligence. Preciso que você crie o código completo de uma dashboard interativa em arquivo único (HTML, CSS via Tailwind e JavaScript) para análise de vendas de veículos da Porsche, utilizando os dados reais fornecidos na planilha anexada.
>
> A dashboard deve ser elegante, moderna, responsiva e utilizar uma paleta de cores sóbria e sofisticada que combine com o mercado de luxo (tons escuros de fundo, detalhes em cinza chumbo e acentos em vermelho esportivo ou dourado discreto).
>
> ### 1. Ingestão e Estrutura dos Dados
> Utilize os dados reais da planilha sanitizada integrada (garantindo que os campos numéricos como `SalesPriceSanitized` e `ModelYearSanitized` sejam lidos corretamente para cálculos, e usando colunas como `PorscheModelSanitized`, `StateSanitized` e `PayMethodSanitized` para as segmentações).
>
> ### 2. Estrutura de KPIs (Topo da Página)
> No topo da dashboard, exiba cartões de destaque (KPI Cards) com:
> 1. **Faturamento Total** (Soma de `SalesPriceSanitized`, formatado em R$/USD)
> 2. **Total de Veículos Vendidos** (Contagem total de registros de vendas)
> 3. **Ticket Médio Geral** (Média de preço por veículo)
>
> ### 3. Perguntas de Negócio Respondidas (Gráficos)
> A dashboard deve conter componentes visuais limpos (usando Chart.js via CDN) que respondam diretamente a estas 3 perguntas estratégicas baseadas na planilha:
> 
> 1. **Concentração Geográfica (Faturamento por Estado):** Um gráfico de barras horizontais exibindo o faturamento total acumulado por `StateSanitized`, permitindo visualizar os principais estados compradores.
> 2. **Mix de Produtos (Volume vs. Receita por Modelo):** Um gráfico de rosca (*doughnut*) mostrando a participação percentual dos principais modelos (`PorscheModelSanitized`) no faturamento total da marca.
> 3. **Liquidez e Comportamento de Compra (Método de Pagamento):** Um gráfico de colunas ou barras mostrando a distribuição dos métodos de pagamento (`PayMethodSanitized`) utilizados pelos clientes (ex: Financiamento, À Vista/Cash, Wire Transfer, etc.).
>
> ### 4. Sistema de Filtros Interativos
> No topo da página, inclua controles interativos (dropdowns) alimentados dinamicamente com os dados para filtrar por:
> - **Ano do Modelo** (`ModelYearSanitized`)
> - **Estado** (`StateSanitized`)
> - **Modelo** (`PorscheModelSanitized`)
> - **Método de Pagamento** (`PayMethodSanitized`)
> 
> **Regra Crítica de Interatividade:** Sempre que o usuário alterar qualquer filtro, os cartões de KPI e todos os gráficos devem ser recalculados e atualizados instantaneamente em tempo real na tela, sem recarregar a página.
>
> ### 5. Requisitos de Entrega
> - Entregue o código completo em um único bloco de HTML limpo, comentado e pronto para ser copiado, salvo como `index.html` e executado diretamente no navegador.
> - Não utilize explicações excessivas antes ou depois do código; foque em entregar a estrutura robusta e funcional.

---

## 🛠️ 4. Detalhes Técnicos do Dashboard

O arquivo `index.html` gerado incorpora:
* **Tailwind CSS (via CDN):** Para estilização e layout responsivo focado na estética *dark mode* de luxo.
* **Chart.js (via CDN):** Renderizando as visualizações de barras e rosca baseadas nos dados.
* **JavaScript Nativo:** Filtragem e atualização dinâmica dos gráficos baseada nas seleções (Ano, Estado, Modelo, Método de Pagamento) feitas pelo usuário na interface.

---

## 🌐 5. Dashboard Publicada

Acesse a dashboard funcionando e explore os filtros interativos no endereço abaixo:

👉 https://gabsgavs.github.io/dashboard_porsche/