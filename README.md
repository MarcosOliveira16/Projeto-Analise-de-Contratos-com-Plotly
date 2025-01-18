# Projeto: Análise de Contratos com Plotly

Este projeto utiliza Python e bibliotecas como `pandas`, `numpy` e `plotly` para análise e visualização de dados relacionados à duração e status de contratos.

---

## Estrutura do Projeto

O notebook contém as seguintes seções principais:

- # Python Insights - Analisando Dados com Python
- ### Case - Cancelamento de Clientes
- # Passo a Passo
- ```python
# Passo 1: importar a base de dados
# Passo 2: visualizar a base de dados (entender a base + identif...
```
- # Passo 1: Importar a base de dados
- ```python
# passo 1: importar a base dados

# instalar as bibliotecas necessárias via cedula
# !pip install pa...
```
- # Passo 2: Visualizar a base de dados (entender a base + identificar problemas)
- ```python
# Primeiro: corrigir valores vazios

# vendo infos da tabela
# comparar a tabela com o numero maior ...
```
- # Passo 3: Corrigir os problemas da base de dados (tratamento de dados)
- ```python
# como o número de resgistro com dados faltantes é muito pequeno, podemos excluir estas linhas
# out...
```
- # Passo 4: Análise Inicial -> quantos clientes cancelaram e qual o % de clientes
- ```python
# contar os valores na coluna 'cancelou'

display(tabela["cancelou"].value_counts())
# resultado do ...
```
- # Passo 5: Análise de causa de cancelamento dos clientes (comparar as outras colunas da tabela com a coluna de cancelamento)
- ```python
import plotly.express as px

# gráficos

# 1. criar o gráfico
# (base de dados, eixo x)
grafico = px...
```
- ```python
# automatizando o processo de análise - ver tds os gráficos de uma vez

import plotly.express as px
...
```
- ```python
# usuarios do contrato mensal sempre cancelam
    # evitar o contrato mensal e incentivar (com desco...
```
- ```python
# usuarios do contrato mensal sempre cancelam
    # evitar o contrato mensal e incentivar (com desco...
```
- ```python
# usuarios do contrato mensal sempre cancelam
    # evitar o contrato mensal e incentivar (com desco...
```
- ```python
# usuarios do contrato mensal sempre cancelam
    # evitar o contrato mensal e incentivar (com desco...
```


---

## Instruções para Execução

1. Certifique-se de ter o Python instalado (recomenda-se a versão 3.10 ou superior).
2. Instale as dependências necessárias com o seguinte comando:

```bash
pip install -r requirements.txt
```

3. Abra o arquivo Jupyter Notebook (`app.ipynb`) com o Jupyter ou VS Code.

---

## Funcionalidades Principais

- **Visualização de Dados**: Utiliza o Plotly para criar gráficos interativos, incluindo histogramas.
- **Análise de Contratos**: Exibe o status dos contratos com cores distintas (azul para cancelado, laranja para não cancelado).
- **Facilidade de Integração**: Possibilidade de personalização com dados externos.

---

## Exemplo de Uso

```python
import plotly.express as px

grafico = px.histogram(
    tabela,
    x="duracao_contrato",
    color="cancelou",
    text_auto=True,
    color_discrete_map={
        "1.0": "blue",
        "0.0": "orange"
    }
)
grafico.show()
```

---

## Autor

- **Marcos Rafael Araújo Oliveira**

---

## Licença

Este projeto é distribuído sob a licença MIT. Consulte o arquivo `LICENSE` para mais informações.

