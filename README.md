# 🚀 Projeto de IA: Previsão de "No-Shows" em Consultas Médicas

Este projeto utiliza Redes Neurais (MLP - Multi-layer Perceptron) para
analisar e prever a probabilidade de um paciente faltar (dar "no-show")
a uma consulta médica.

O objetivo principal foi aplicar os conceitos de deep learning em um
dataset do mundo real, cobrindo todo o ciclo de vida do projeto: desde a
limpeza e engenharia de features até o treinamento e, o mais importante,
a análise crítica dos resultados de um modelo.

**Autor:** Luiz G. F. Carvalho
**Dataset:** *Medical Appointment No-Shows* (Kaggle)

------------------------------------------------------------------------

## 🎯 O Problema

O "no-show" (ausência de pacientes) é um problema de gestão caro e
crônico em sistemas de saúde. Ele gera ociosidade em equipamentos
médicos caros (como tomógrafos) e no tempo dos profissionais de saúde,
além de aumentar as filas de espera.

Este projeto busca responder:

> **É possível, usando um modelo MLP simples, prever com antecedência
> quais pacientes têm maior probabilidade de faltar?**

------------------------------------------------------------------------

## 🛠️ Metodologia e Ferramentas

O projeto foi desenvolvido em **Python 3** e estruturado em um
**notebook Jupyter (.ipynb)**.

### Bibliotecas Utilizadas

-   **Pandas** -- manipulação e limpeza de dados
-   **Scikit-learn** -- pré-processamento, divisão de dados e métricas
-   **TensorFlow / Keras** -- construção e treinamento da rede neural
-   **Matplotlib** -- visualização do aprendizado

### Fluxo do Projeto

1.  **Carga e Limpeza:**
    Normalização de nomes das colunas e interpretação de datas.

2.  **Engenharia de Features:**

    -   Conversão de categorias (Gender)
    -   Cálculo de `WaitingDays`
    -   Extração do dia da semana (`AppointmentDayOfWeek`)

3.  **Pré-processamento:**
    Normalização com `StandardScaler`.

4.  **Modelo MLP:**

    -   `Dense(32, relu)`
    -   `Dense(16, relu)`
    -   `Dense(1, sigmoid)`

5.  **Treinamento:**

    -   Otimizador: `adam`
    -   Função de perda: `binary_crossentropy`
    -   10 épocas

------------------------------------------------------------------------

## 📊 Análise Crítica --- A Descoberta Principal

O modelo atingiu aproximadamente **80% de acurácia**, porém essa métrica
é **enganosa**, pois o dataset é altamente desbalanceado: cerca de **80%
comparecem**.

### 📉 Relatório de Classificação

                   precision    recall  f1-score   support

    Compareceu (0)       0.80      1.00      0.89     17642
    Faltou (1)           0.56      0.01      0.02      4464

### ❗ Conclusão-Chave

O modelo "**trapaceou**" ao prever "Compareceu" para quase todos os
pacientes.
O recall da classe **Faltou** foi de apenas **1%**, identificando apenas
**53 de 4.464** ausências reais.

> **Portanto, o modelo é inviável para o propósito de negócio.**

------------------------------------------------------------------------

## 💡 Discussão e Aplicações na Engenharia

A principal descoberta foi a **falha**, não o sucesso: o modelo não
consegue lidar com o desbalanceamento.

### Aplicações se o modelo funcionasse:

-   **Engenharia de Produção/Operações:** otimizar o uso de recursos de
    saúde.
-   **Engenharia de Software:** sistemas automáticos que disparam
    lembretes ou confirmam consultas apenas para pacientes com alto
    risco de faltar.

------------------------------------------------------------------------

## ⚙️ Como Executar Este Projeto

### 1. Clonar o repositório

``` bash
git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
```

### 2. Criar ambiente virtual

``` bash
cd PROJETO-INTELIGENCIA
python -m venv venv
```

### 3. Ativar ambiente

``` bash
.env\Scriptsctivate
```

### 4. Instalar dependências

``` bash
pip install -r requirements.txt
```

### 5. Abrir o notebook

Abra **notebooks/analise_no_shows.ipynb** no VS Code ou Jupyter.

------------------------------------------------------------------------

## 🧾 Licença

Este projeto é apenas educacional e não deve ser utilizado para decisões
clínicas reais.
