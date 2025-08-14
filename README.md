# TelecomX_Churn_Analysis

[![Notebook](https://img.shields.io/badge/notebook-Colab-blue)]()
[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey)]()

# 📊 Análise Estratégica: TelecomX — Churn (Evasão de Clientes)

## 🌟 Visão Executiva

**Objetivo Principal:**  
Identificar os drivers da evasão (churn) na base de clientes da TelecomX e sugerir ações operacionais e analíticas para reduzir a taxa de cancelamento e aumentar retenção/LTV.

**Contexto:**  
Projeto desenvolvido como segundo Challenge de Data Science Oracle + Alura, combinando técnicas analíticas com storytelling e ETL para decisão estratégica.

Projeto desenvolvido a partir de um conjunto de dados públicos (`TelecomX_Data.json`) hospedado no GitHub. O trabalho inclui um pipeline ETL reproducível, Análise Exploratória (EDA), testes estatísticos simples e recomendações de negócio.

---
### 📈 Pipeline de Análise (resumo)
1. **Extração:** leitura do JSON no GitHub e normalização via `pd.json_normalize(..., sep='_')`.  
2. **Transformação:** padronização de nomes (`snake_case`), conversão de tipos, tratamento de valores ausentes e criação de features (ex.: `account_charges_daily`, flags de serviço).  
3. **Carga:** persistência de arquivo tratado (`parquet`) em `data/`.  
4. **EDA & Visualização:** gráficos com `matplotlib`/`seaborn` (um gráfico por célula do notebook para clareza).  
5. **Estatística básica & Baseline:** testes qui-quadrado para categóricas, correlações ponto-biserial para numéricas, regressão logística explicativa (baseline).  
6. **Relatório:** síntese executiva com recomendações acionáveis.

---

## 📊 Resultados Quantitativos (números-chave)

**Base:** 7.267 clientes

| Métrica | Valor |
|---|---:|
| Churn (informado) | **~25,7%** |
| Churn não informado | **~3,1%** |
| Senior (churn) | **40,3%** (vs 22,9% não-senior) |
| Contrato — Month-to-month | **41,3%** |
| Contrato — One year | **10,9%** |
| Contrato — Two year | **2,8%** |
| Internet — Fiber optic | **41,2%** |
| Internet — DSL | **19,3%** |
| Internet — No | **8,4%** |
| Pagamento — Electronic check | **44,3%** |
| Pagamento — Credit card (auto) | **15,7%** |
| Pagamento — Bank transfer (auto) | **17,3%** |
| Pagamento — Mailed check | **19,6%** |
| Correlação churn × tenure | **r = −0.341** |
| Correlação churn × monthly charges | **r = +0.183** |
| Correlação churn × total charges | **r = −0.194** |

> Observação: números acima extraídos das análises do notebook — ver seção *Apêndice* para tabelas e extração completa.

---

## 🛠 Como rodar o projeto

### 1) Clonar o repositório

```bash
git clone https://github.com/BrunoRomeu/Telecom_X_Churn_Analise_Completa_Alura.git
cd Telecom_X_Churn_Analise_Completa_Alura
```

### 2) Rodar no Colab

1. Acesse: [Google Colab](https://colab.research.google.com)
2. File → Open notebook → GitHub → cole `https://github.com/BrunoRomeu/Telecom_X_Churn_Analise_Completa_Alura`
3. Selecione `notebook/TelecomX_Churn_Analise_Final.ipynb` e execute.
---
## ✅ Principais conclusões (resumido)

* **Contrastante driver**: contratos *Month-to-month* concentram a maior parte do churn.
* **Segmentos de risco**: clientes sênior, usuários de *fiber*, clientes pagantes via `Electronic check`, e clientes com *tenure* baixo.
* **Paradoxo do valor**: gasto mensal ↑ → risco ↑ (curto prazo); gasto acumulado ↑ → risco ↓ (clientes maduros fidelizados).

---

## 💡 Recomendações de Negócio (prioridade)

1. **Campanha de migração contratual** (M2M → 1/2 ano) priorizando tenure 2–10 meses e high-ARPU.
2. **Onboarding intensivo** (0–90 dias): call, checagem técnica e fast-track suporte.
3. **Task-force Fibra**: monitoramento proativo e SLA mais agressivo.
4. **Rever fluxo de Electronic check**: reduzir atritos, incentivar autopay (CC/Debit).
5. **Modelo preditivo & ações automatizadas** (score semanal + playbooks de retenção).

---

## 🔎 Limitações

* Análises univariadas predominantes — necessidade de confirmação por modelos multivariados (logística/XGBoost) e por análise de sobrevivência (Kaplan-Meier/Cox).
* Churn com 3.1% “não informado” — estes registros foram marcados como `churn_missing` e não foram imputados arbitrariamente para evitar viés no target.
* O dataset é um *challenge* (dados sintéticos/anonimizados) — recomenda-se validar hipóteses contra dados de produção.

---

## 📚 Reprodutibilidade & Contribuição

Contribuições, issues e PRs são bem-vindos — siga o padrão:

1. Fork → branch feature → PR.
2. Documente mudanças no `CHANGELOG.md` (se aplicável).
3. Para dados sensíveis, use `.env` e nunca comite credenciais.

---

## 🧾 Licença

**Creative Commons BY-NC-SA 4.0** — ver `LICENSE` para detalhes.

---

## ✉️ Autor & Contato

**Autor:** Bruno Romeu  
**Contato:** [LinkedIn](https://www.linkedin.com/in/bruno-celestino-romeu/) | [GitHub](https://github.com/BrunoRomeu)  
**Licença:** Creative Commons BY-NC-SA 4.0  

> "Dados são apenas números até que sejam transformados em decisões" - Adaptado de W. Edwards Deming
