# 📚 O Mito do Tijolaço: Livros Longos são Melhores ou Apenas Mais Tolerados?

Análise exploratória e estatística de dados do catálogo do Goodreads para investigar a relação entre o tamanho da obra (número de páginas), a satisfação do leitor (nota média) e o volume de engajamento.

---

## 📌 Sobre o Projeto

O senso comum no mercado editorial sugere que livros volumosos ("tijolaços") enfrentam maior resistência do público. No entanto, surge a seguinte dúvida: **obras extensas recebem notas mais altas porque são genuinamente superiores, ou porque a barreira de entrada filtra leitores casuais, mantendo apenas fãs engajados?**

Este projeto analisa milhares de registros do dataset *Goodreads Books* utilizando Python e bibliotecas de análise de dados para responder a essa pergunta com suporte visual e estatístico.

---

## ❓ Perguntas Chave & Hipótese

1. **Percepção de Valor:** Livros com mais de 600 páginas possuem notas médias mais altas do que livros curtos (< 200 páginas)?
2. **Engajamento & Barreira de Entrada:** O volume total de avaliações cai conforme o número de páginas aumenta?
3. **Consenso vs. Dispersão:** A variação de notas é menor em livros longos do que em livros curtos?

* **Hipótese Central:** Livros longos passam por um **viés de autoseleção**. Leitores não engajados abandonam a leitura antes de avaliar, resultando em notas médias mais altas e com menor variabilidade.

---

## 🛠️ Tecnologias e Ferramentas

* **Linguagem:** Python 3.x
* **Manipulação de Dados:** Pandas
* **Visualização de Dados:** Seaborn, Matplotlib
* **Ambiente de Desenvolvimento:** Google Colab / Jupyter Notebook
* **Fonte dos Dados:** [Goodreads Books (Kaggle)](https://www.kaggle.com/datasets/jealousleopard/goodreadsbooks)

---

## 📂 Tratamento de Dados (Data Cleaning)

Para garantir a qualidade da análise, a base original passou pelo seguinte fluxo de limpeza:

* **Remoção de Inconsistências:** Filtragem de linhas com erros de parsing de delimitador e valores ausentes nas colunas críticas (`num_pages`, `average_rating`, `ratings_count`).
* **Filtro de Relevância:** Manutenção de livros com `num_pages > 0` e no mínimo `10` avaliações para eliminar registros irrisórios ou testes.
* **Categorização em Bins (Faixas de Páginas):**
  * `Curto`: < 200 páginas
  * `Médio`: 200 a 400 páginas
  * `Longo`: 400 a 600 páginas
  * `Tijolaço`: > 600 páginas

---

## 📊 Resultados e Métricas Principais

### Tabela Resumo das Categoria

| Faixa de Páginas | Total de Livros | Nota Média | Mediana de Avaliações | Média de Avaliações |
| :--- | :---: | :---: | :---: | :---: |
| **Curto (< 200p)** | *2.528* | **3.94** | *414* | *11.477* |
| **Médio (200-400p)** | *4.874* | **3.90** | *1.220* | *19.759* |
| **Longo (400-600p)** | *1.969* | **3.98** | *1.400* | *25.449* |
| **Tijolaço (> 600p)** | *1.024* | **4.11** | *1.050* | *23.551* |

---

### 📈 Análise Visual

#### 1. Painel Comparativo: Nota Média vs. Volume de Avaliações
<img width="4750" height="1449" alt="mito_do_tijolaco_painel" src="https://github.com/user-attachments/assets/eb856358-9e4a-4020-bb47-30bee2ca4397" />


> **Insight:** A nota média apresenta crescimento constante da faixa *Curto* para a faixa *Tijolaço*. Em contrapartida, a mediana de avaliações diminui nas obras mais extensas, confirmando a existência de uma barreira de entrada para o leitor médio.

---

#### 2. Relação Direta e Dispersão Estatística
<img width="4750" height="1750" alt="relacao_e_dispersao_paginas" src="https://github.com/user-attachments/assets/46285397-d604-476d-9e97-d5892eea504d" />


* **Scatter Plot (Esquerda):** A linha de regressão apresenta inclinação positiva contínua. Entre 600 e 1.200 páginas, a incidência de notas abaixo de 3.5 é praticamente nula.
* **Boxplot (Direita):** A mediana desloca-se progressivamente para o topo da escala, enquanto o intervalo interquartil (corpo do caixa) torna-se mais compacto em *Tijolaço*, evidenciando alto consenso entre os leitores.

---

## 📐 Validação Estatística

O Coeficiente de Correlação de Pearson ($r$) calculado entre o número de páginas e a nota média resultou em:

$$r \approx 0.15$$

Em bases comportamentais de grande volume, um coeficiente positivo entre **0.10 e 0.25** confirma uma **correlação positiva fraca a moderada**, validando quantitativamente a tendência ascendente identificada nos gráficos.

---

## 💡 Conclusão de Negócio

1. **O "Mito" foi Desmistificado:** Livros longos não recebem punição dos leitores por seu tamanho; pelo contrário, possuem médias de avaliação superiores.
2. **Efeito Filtro:** O volume reduzido de leitores em livros extensos atua como um filtro natural. Apenas leitores altamente alinhados com o tema concluem a obra e atribuem nota.
3. **Recomendação para o Mercado Editorial:** Obras extensas possuem público fiel e altamente satisfeito. Estratégias de marketing podem focar no nicho especializado em vez de tentar transformar "tijolaços" em apelos de massa.

---

## 🚀 Como Executar o Projeto

1. Clone este repositório:
   ```bash
   git clone [https://github.com/andradisa/o-mito-do-tijolaco.git](https://github.com/andradisa/o-mito-do-tijolaco.git)
