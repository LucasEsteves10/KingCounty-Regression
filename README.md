# Análise de Regressão: Fatores que Influenciam o Preço de Imóveis

## 🚀 Visão Geral do Projeto

Este projeto utiliza um modelo de Regressão Linear Múltipla para investigar os principais fatores que determinam o preço de venda de imóveis em King County, WA (EUA), região que inclui a cidade de Seattle. A análise foi desenvolvida inteiramente em R, com foco na interpretação dos coeficientes, diagnóstico do modelo e validação das suposições estatísticas.

O modelo final alcançou um **R² ajustado de 0.764**, demonstrando um bom poder explicativo sobre a variação dos preços.

**Fonte dos Dados:** [House Sales in King County, USA (Kaggle)](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction)

## 🎯 Objetivos

* **Objetivo Principal:** Identificar e quantificar o impacto das características estruturais, geográficas e de conservação no preço de venda dos imóveis.
* **Objetivos Secundários:**
    * Analisar o efeito de interações entre variáveis (ex: idade vs. condição do imóvel).
    * Avaliar a adequação do modelo de regressão linear e validar seus pressupostos.
    * Construir um modelo preditivo robusto a partir das variáveis mais significativas.

## 🛠️ Ferramentas e Bibliotecas

* **Linguagem:** R
* **Ambiente:** RStudio
* **Bibliotecas Principais:**
    * `dplyr`: Manipulação e pré-processamento de dados
    * `ggplot2`: Criação de visualizações
    * `sf`: Análise de dados geoespaciais
    * `car`: Diagnóstico do modelo (cálculo do VIF)
    * `sjPlot`: Visualização de resultados de modelos de regressão
    * `caret`: Treinamento e avaliação de modelos

## 📊 Metodologia

O projeto foi estruturado nas seguintes etapas:

1.  **Pré-processamento:** Foram criadas novas variáveis, como a idade do imóvel (`house_age`). A variável resposta `price` apresentou forte assimetria, sendo transformada para `log(price)` para estabilizar a variância e linearizar as relações, atendendo melhor aos pressupostos do modelo.
2.  **Análise Exploratória:** A distribuição espacial dos preços foi analisada, revelando uma forte concentração de imóveis de alto valor em áreas próximas a corpos d'água e centros urbanos.
3.  **Modelagem:** Foi ajustado um modelo de regressão linear múltipla. O processo de seleção de variáveis foi guiado pelo critério AIC (Akaike Information Criterion) e pela significância estatística dos preditores.
4.  **Diagnóstico do Modelo:** Foram realizados testes para validar os pressupostos do modelo, incluindo:
    * **Análise de Resíduos:** Verificação de homocedasticidade (variância constante) e normalidade.
    * **Multicolinearidade:** O Fator de Inflação de Variância (VIF) foi calculado para todas as variáveis, não indicando problemas de colinearidade.
    * **Pontos Influentes:** Análise da Distância de Cook para identificar outliers com alta alavancagem.

## 📈 Principais Resultados e Descobertas

O modelo final conseguiu explicar **76.4%** da variação no logaritmo do preço dos imóveis.

### Fatores de Maior Impacto no Preço:
* **Qualidade da Construção (`grade`):** O fator mais influente. Cada ponto adicional na escala de qualidade aumenta o preço em aproximadamente **18.6%**.
* **Área Útil (`sqft_living`):** Um aumento de 1% na área útil da casa está associado a um aumento de **0.41%** no preço.
* **Localização (Latitude):** A localização geográfica (especificamente a latitude) é um forte preditor de valor, indicando zonas mais valorizadas ao norte do condado.
* **Vista para a Água (`waterfront`):** Imóveis com vista para a água são, em média, **39.8%** mais caros.

### Visualização Chave: Distribuição Geográfica dos Preços
O mapa abaixo ilustra a concentração de imóveis de alto valor (>1M) em regiões específicas, validando a importância das variáveis de localização no modelo.

![Distribuição de Imóveis por Preço](images/mapa_preco_imoveis.png)

### Interação Relevante: Idade vs. Condição
A análise revelou uma interação significativa entre a idade do imóvel e sua condição. Enquanto imóveis em más condições perdem valor com o tempo, aqueles em **boas condições podem até se valorizar com o passar dos anos**, como mostra o gráfico de efeitos preditos.

## 🚀 Como Executar o Projeto

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git](https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git)
    ```
2.  Abra o arquivo `relatorio.Rmd` ou `TRABALHO_REGRESSÃO.Rmd` no RStudio.
3.  Certifique-se de que o arquivo de dados `kc_house_data.csv` esteja na subpasta `data/`.
4.  Instale as bibliotecas necessárias, que estão listadas no início do script.
5.  Execute os blocos de código (*chunks*) ou utilize o botão "Knit" para gerar o relatório completo.
