# Python Insights - Analisando Dados com Python

### Case - Cancelamento de Clientes

Você foi contratado por uma empresa com mais de 800 mil clientes para um projeto de Dados. Recentemente a empresa percebeu que da sua base total de clientes, a maioria são clientes inativos, ou seja, que já cancelaram o serviço.

Precisando melhorar seus resultados, a empresa quer entender os principais motivos desses cancelamentos e quais as ações mais eficientes para reduzir esse número.

### Base de Dados
O arquivo usado e que deve ser importado para o ambiente é o 'cancelamentos.csv', encontrado neste repositório.

## Passo a Passo

### Passo 1: Importar a Base de Dados

Primeiramente, instalamos as bibliotecas necessárias:
```bash
# Via célula do Jupyter Notebook
!pip install pandas numpy openpyxl plotly

# Via terminal
pip install pandas numpy openpyxl plotly
```

Em seguida, carregamos a base de dados:
```python
import pandas as pd

tabela = pd.read_csv("cancelamentos.csv")

# Removendo a coluna irrelevante "CustomerID"
tabela = tabela.drop(columns="CustomerID")

# Exibindo a tabela
display(tabela)
```

### Passo 2: Visualizar a Base de Dados

Antes de qualquer análise, verificamos as informações da tabela:
```python
# Verificando informações gerais
print(tabela.info())
```
Isso nos permite identificar possíveis valores faltantes ou inconsistências nos dados.

### Passo 3: Tratamento de Dados

Removemos valores ausentes, já que eles representam uma pequena parte da base:
```python
# Removendo linhas com valores ausentes
tabela = tabela.dropna()

# Confirmando o novo tamanho da tabela
print(tabela.info())
```

### Passo 4: Análise Inicial

Contamos os valores na coluna `cancelou` para identificar a quantidade e o percentual de clientes que cancelaram:
```python
# Contagem dos valores
display(tabela["cancelou"].value_counts())

# Percentuais
display(tabela["cancelou"].value_counts(normalize=True))
```

Resultados:
- 56% dos clientes cancelaram
- 43% dos clientes não cancelaram

### Passo 5: Análise de Causa de Cancelamento

Utilizamos gráficos para analisar como diferentes variáveis influenciam o cancelamento:
```python
import plotly.express as px

# Criando gráficos para cada coluna
for coluna in tabela.columns:
    grafico = px.histogram(tabela, x=coluna, color="cancelou", text_auto=True)
    grafico.show()
```

#### Observações:
1. Usuários de contrato mensal têm maior propensão a cancelar.
2. Usuários que ligaram mais de 4 vezes para o call center geralmente cancelaram.
3. Usuários com atraso de pagamento superior a 20 dias também tendem a cancelar.

### Passo 6: Propostas de Soluções

Com base na análise, aplicamos filtros para mitigar os principais problemas:
```python
# Removendo contratos mensais
tabela = tabela[tabela['duracao_contrato'] != "Monthly"]

# Mantendo usuários com até 4 ligações para o call center
tabela = tabela[tabela['ligacoes_callcenter'] <= 4]

# Mantendo usuários com atraso de pagamento de até 20 dias
tabela = tabela[tabela['dias_atraso'] <= 20]

# Resultados finais
display(tabela["cancelou"].value_counts())
display(tabela["cancelou"].value_counts(normalize=True))
```

### Conclusões

- Contratos anuais e trimestrais devem ser incentivados com descontos.
- Monitorar clientes com mais de 3 chamadas para o call center para ações preventivas.
- Criar alertas para atrasos superiores a 15 dias.

Essa análise demonstra que a combinação de ajustes contratuais, atendimento proativo e políticas de cobrança pode reduzir significativamente o número de cancelamentos.

