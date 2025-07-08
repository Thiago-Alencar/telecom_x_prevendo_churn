# Telecom X - Parte 2: Prevendo a Evasão de Clientes com Machine Learning

![Status do Projeto](https://img.shields.io/badge/Status-Concluído-brightgreen)
![Linguagem](https://img.shields.io/badge/Python-3.x-blue)
![Bibliotecas](https://img.shields.io/badge/Bibliotecas-Scikit--Learn%20%7C%20Pandas%20%7C%20Imbalanced--learn-orange)

## 📖 Descrição do Projeto

Esta é a segunda fase do projeto de análise de dados da **Telecom X**. Após uma análise exploratória bem-sucedida, o foco agora é no desenvolvimento de um **pipeline de Machine Learning** para prever quais clientes têm a maior probabilidade de cancelar seus serviços (churn).

O objetivo é passar de uma análise descritiva para uma **análise preditiva**, criando uma ferramenta que permita à empresa antecipar a evasão e agir de forma proativa para reter seus clientes.

## 🎯 Missão

Construir um pipeline de modelagem robusto, desde o pré-processamento dos dados até a avaliação e interpretação de modelos de classificação, para identificar os principais fatores de risco da evasão e gerar insights acionáveis para o negócio.

## 🛠️ Ferramentas e Bibliotecas

* **Análise e Manipulação de Dados:** `pandas`, `numpy`
* **Visualização de Dados:** `matplotlib`, `seaborn`
* **Machine Learning e Pré-processamento:** `scikit-learn`
* **Balanceamento de Classes:** `imbalanced-learn`

## Pipeline de Machine Learning

O projeto foi estruturado em um fluxo de trabalho completo, seguindo as melhores práticas para modelagem preditiva:

#### 1. Preparação dos Dados
* **Extração:** Carregamento do dataset tratado na fase anterior.
* **Limpeza:** Remoção de colunas irrelevantes (`customerID`).
* **Encoding:** Conversão de variáveis categóricas para formato numérico utilizando One-Hot Encoding (`pd.get_dummies`).
* **Análise de Desequilíbrio:** Verificação da proporção entre as classes da variável alvo (`Churn`), constatando a necessidade de balanceamento.

#### 2. Modelagem
* **Divisão dos Dados:** Separação do dataset em conjuntos de treino (80%) e teste (20%) de forma estratificada.
* **Padronização:** Aplicação do `StandardScaler` nos dados para normalizar a escala das features, essencial para modelos como a Regressão Logística.
* **Balanceamento:** Uso da técnica **SMOTE** (Synthetic Minority Over-sampling Technique) **apenas nos dados de treino** para corrigir o desequilíbrio de classes e evitar viés no modelo.
* **Treinamento:** Construção e treinamento de dois modelos de classificação:
    1.  **Regressão Logística:** Um modelo linear, rápido e interpretável.
    2.  **Random Forest:** Um modelo de ensemble robusto e de alta performance.

#### 3. Avaliação e Interpretação
* **Métricas de Desempenho:** Avaliação dos modelos no conjunto de teste com Acurácia, Precisão, Recall, F1-Score e Matriz de Confusão.
* **Análise de Variáveis:** Extração da importância das features (`feature_importance_`) do Random Forest e dos coeficientes da Regressão Logística para entender os drivers do churn.
* **Conclusão Estratégica:** Consolidação dos resultados para gerar insights e recomendações de negócio.

## 📊 Desempenho dos Modelos

O modelo **Random Forest** apresentou uma performance superior, sendo a escolha recomendada para a implantação.

| Métrica (Classe 1 - Churn) | Regressão Logística | Random Forest |
| :------------------------- | :------------------ | :------------ |
| **Precisão** | 0.52                | 0.59          |
| **Recall** | 0.77                | 0.74          |
| **F1-Score** | 0.62                | **0.66** |
| **Acurácia Geral** | 0.75                | **0.79** |

O **Recall** mais alto na Regressão Logística foi obtido ao custo de uma precisão muito baixa. O **F1-Score** do Random Forest mostra o melhor equilíbrio entre identificar corretamente os clientes que evadem e não classificar incorretamente os clientes fiéis.

## 🧠 Principais Fatores de Evasão

A análise de importância das variáveis em ambos os modelos foi consistente, apontando para os seguintes fatores como os mais críticos:

1.  **Tipo de Contrato (`account_Contract_Month-to-month`):** O principal indicador de risco.
2.  **Tempo de Contrato (`customer_tenure`):** Clientes novos têm uma chance de churn drasticamente maior.
3.  **Serviço de Internet (`internet_InternetService_Fiber optic`):** Clientes com fibra óptica são mais propensos a cancelar.
4.  **Ausência de Suporte Técnico (`internet_TechSupport_No`):** A falta de um serviço de suporte claro aumenta o risco.
5.  **Cobranças Mensais (`account_Charges_Monthly`):** Faturas mais altas estão correlacionadas com maior evasão.

## 🚀 Recomendações Estratégicas

Com base nos insights do modelo, as seguintes estratégias de retenção são propostas:

* **Campanhas de Migração de Plano:** Oferecer incentivos para clientes de alto risco com contrato mensal migrarem para planos anuais.
* **Programa de Onboarding (Boas-Vindas):** Implementar um acompanhamento ativo nos primeiros 90 dias para clientes novos identificados pelo modelo como de alto risco.
* **Oferta de Valor Agregado:** Para clientes de Fibra Óptica com alto score de churn, oferecer pacotes de serviços como Suporte Técnico e Segurança Online para aumentar o engajamento e o valor percebido.

## ⚙️ Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/Thiago-Alencar/telecom_x_prevendo_churn/](https://github.com/Thiago-Alencar/telecom_x_prevendo_churn/)
    ```
2.  **Navegue até o diretório:**
    ```bash
    cd seu-repositorio
    ```
3.  **Instale as dependências** (recomenda-se criar um ambiente virtual):
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
    ```
4.  **Execute o notebook**: Abra o arquivo `.ipynb` no Jupyter Notebook, Jupyter Lab ou Google Colab e execute as células em ordem.

## 👨‍💻 Autor

Projeto desenvolvido por **Thiago Alencar Antonio**.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/thiago-alencar-antonio/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Thiago-Alencar/)
