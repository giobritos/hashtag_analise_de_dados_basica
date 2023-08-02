# Projeto de Análise de Dados Básica

Este é um projeto de análise de dados básica utilizando as bibliotecas Pandas e Plotly com base no projeto do Professor João Paulo Rodrigues de Lira da Hashtag Treinamentos. O objetivo deste projeto é explorar e visualizar dados de uma base de dados utilizando análise estatística e gráficos.

## Visão Geral

Neste projeto, iremos realizar uma análise exploratória de uma base de dados utilizando as bibliotecas Pandas e Plotly. A base de dados utilizada contém informações sobre usuários de serviços de telecomunicação e seus respectivos contratos.

Link Original da base de dados do Kaggle: [Telecom Users Dataset](https://www.kaggle.com/radmirzosimov/telecom-users-dataset)

## Instalação das Bibliotecas

Antes de começar, certifique-se de ter instalado as bibliotecas Pandas e Plotly. Se ainda não as tiver instalado, você pode fazê-lo com os seguintes comandos:

```bash
!pip install pandas
!pip install plotly
```

## Importando a Base de Dados

Para iniciar nossa análise, importamos a base de dados utilizando a biblioteca Pandas:

```python
import pandas as pd

tabela = pd.read_csv("telecom_users.csv")
```

## Limpeza e Preparação dos Dados

Após a importação, realizamos algumas etapas de limpeza e preparação dos dados:

1. Removemos colunas desnecessárias: `Unnamed: 0` e `IDCliente`.
2. Convertemos a coluna `TotalGasto` para o tipo numérico.
3. Removemos linhas vazias.

```python
tabela = tabela.drop(["Unnamed: 0", "IDCliente"], axis=1)
tabela["TotalGasto"] = pd.to_numeric(tabela["TotalGasto"], errors="coerce")
tabela = tabela.dropna(how="all", axis=1)
tabela = tabela.dropna(how="any", axis=0)
```

## Análise de Dados

Realizamos uma análise inicial dos dados, verificando a proporção de cancelamento (Churn) na base de dados:

```python
churn_count = tabela["Churn"].value_counts()
churn_percentage = tabela["Churn"].value_counts(normalize=True).map("{:.1%}".format)
print(churn_count)
print(churn_percentage)
```

## Visualização de Dados

Utilizamos a biblioteca Plotly para criar gráficos que nos ajudem a visualizar as informações de maneira mais clara:

1. Histogramas para comparar cada coluna da tabela com a coluna de cancelamento (Churn).
   
```python
import plotly.express as px

for coluna in tabela.columns:
    grafico = px.histogram(tabela, x=coluna, color="Churn")
    grafico.show()
```

## Conclusões e Insights

Com base na análise e visualização dos dados, podemos tirar algumas conclusões e obter insights para tomada de decisões:

1. Proporção de cancelamento (Churn) é alta para clientes com poucos meses de contrato.
   - **Insight:** Investir em melhorias no atendimento ao cliente no início do contrato.

2. Métodos automáticos de pagamento têm menor taxa de cancelamento.
   - **Insight:** Incentivar o uso de métodos automáticos de pagamento, oferecendo benefícios.

3. Contratos mensais têm taxa de cancelamento superior a outros tipos de contrato.
   - **Insight:** Melhorar as ofertas de contratos anuais para atrair mais clientes.

4. Clientes sem serviços adicionais de suporte técnico, proteção a dispositivos e segurança online tendem a cancelar mais.
   - **Insight:** Investir em melhorias nos serviços de suporte técnico e segurança online.

## Contribuição

Contribuições são bem-vindas! Se você tiver sugestões de melhorias na análise, visualização ou interpretação dos dados, sinta-se à vontade para abrir uma issue neste repositório ou enviar um pull request.

## Agradecimentos

Agradeço ao Professor João Paulo Rodrigues de Lira da Hashtag Treinamentos pelo projeto idealizado e à comunidade de código aberto pelas bibliotecas Pandas e Plotly, que tornaram possível a realização desta análise de dados. 

**Desenvolvido com ❤️ e Python.**
