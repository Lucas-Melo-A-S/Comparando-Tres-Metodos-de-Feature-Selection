
# Feature Selection em Classificação Binária  
## Correlação vs Boruta vs Feature Importance

Este repositório apresenta uma análise comparativa entre **três métodos clássicos de Feature Selection** aplicados a um problema real de **classificação binária de defeitos em software**, utilizando dados públicos do Kaggle.

O objetivo principal é avaliar **como diferentes estratégias de seleção de variáveis impactam o desempenho, a estabilidade e a interpretabilidade dos modelos preditivos**.

---

## 📌 Dataset

- **Fonte:** Kaggle — *Binary Classification with a Software Defects Dataset*
- **Linhas:** 71.234  
- **Variáveis:** 23  
- **Tipo:** Todas numéricas  
- **Valores nulos:** Nenhum  

Como as variáveis apresentam **escalas muito diferentes**, foi aplicada a padronização via **StandardScaler**, evitando que atributos com valores elevados dominassem o processo de modelagem.

---

## 🧠 Por que Feature Selection importa?

A seleção de variáveis é uma etapa crítica em projetos de Machine Learning, pois:

- Reduz ruído
- Diminui overfitting
- Melhora o desempenho dos modelos
- Torna os resultados mais interpretáveis
- Reduz custo computacional

Neste projeto, avaliamos **não apenas a lógica interna de cada método**, mas principalmente **seu impacto real nos modelos preditivos**.

---

## 🔬 Métodos Avaliados

### 1️⃣ Correlação (Filter Method)
- Remove apenas variáveis **altamente correlacionadas entre si** (threshold > 85%)
- Objetivo: evitar redundância mantendo o máximo de informação possível

**Variáveis selecionadas:**

[‘loc’, ‘id’, ‘I’, ‘e’, ‘d’, ‘n’, ‘uniq_Op’, ‘v(g)’,
‘IOBlank’, ‘iv(g)’, ‘ev(g)’, ‘IOComment’, ‘IoCodeAndComment’]

---

### 2️⃣ Boruta (Wrapper Method)
- Método extremamente rigoroso
- Compara a importância real das variáveis com versões aleatórias ("shadow features")
- Mantém apenas variáveis consistentemente relevantes

**Variáveis selecionadas:**

[‘loc’, ‘t’, ‘v’]

---

### 3️⃣ Feature Importance (Embedded Method – Random Forest)
- Baseado na redução de impureza dos splits em modelos de árvore
- Aplicado cutoff de **30% de importância mínima**

**Variáveis selecionadas:**

[‘loc’, ‘v(g)’, ‘iv(g)’, ‘n’, ‘v’, ‘d’, ‘i’, ‘e’, ‘t’,
‘lOCode’, ‘total_Op’, ‘total_Opnd’, ‘branchCount’]

---

## 🤖 Modelos Avaliados

Os conjuntos de variáveis selecionados foram testados em diferentes modelos, com destaque para:

- **XGBoost**
- Regressão Logística
- Random Forest

As métricas analisadas incluem:
- ROC AUC
- Gini
- KS
- Precision–Recall
- Matrizes de confusão
- Gráficos de ordenação por score

---

## 📊 Principais Resultados

### 🔹 Correlação
- **Melhor desempenho geral**
- Maior AUC e Gini
- Curvas ROC e Precision–Recall mais estáveis
- Excelente separação entre classes

➡️ Remover apenas redundâncias preserva informação relevante e favorece modelos complexos.

---

### 🔹 Feature Importance
- Excelente equilíbrio entre desempenho e simplicidade
- XGBoost apresentou alta estabilidade entre treino e teste
- Baixo indício de overfitting

➡️ Ótima escolha quando se busca robustez sem agressividade excessiva.

---

### 🔹 Boruta
- Maior interpretabilidade
- Pequena queda de performance em modelos complexos
- Melhora desempenho de modelos lineares

➡️ Ideal quando explicabilidade é mais importante que performance máxima.

---

## 🧠 Conclusão

Não existe um método universalmente melhor — **a escolha depende do objetivo do projeto**:

| Objetivo | Melhor Método |
|--------|---------------|
| Máximo desempenho | Correlação |
| Equilíbrio desempenho × simplicidade | Feature Importance |
| Interpretabilidade | Boruta |

> **Lição principal:**  
> Métodos simples, quando bem aplicados, podem superar abordagens mais complexas.

---

## 📁 Estrutura do Repositório

    ├── notebooks/
    │   ├── Detecção_de_Problemas_em_Softwares_Correlação.ipynb
    │   ├── Detecção_de_Problemas_em_Softwares_Boruta.ipynb
    │   └── Detecção_de_Problemas_em_Softwares_Feature_Selection.ipynb
    │
    ├── README.md
    
    ---

## 🔗 Notebooks

- 📘 Feature Selection – Random Forest  
- 📘 Boruta  
- 📘 Correlação  

*(Os notebooks contêm todo o pipeline de pré-processamento, seleção de variáveis, modelagem e avaliação.)*

---

## 🙌 Considerações Finais

Este projeto demonstra, na prática, como **decisões de Feature Selection influenciam diretamente o desempenho e a confiabilidade dos modelos de Machine Learning**.

Se tiver dúvidas, sugestões ou quiser discutir melhorias, fique à vontade para abrir uma issue ou comentar.  
Obrigado pela leitura!


⸻
