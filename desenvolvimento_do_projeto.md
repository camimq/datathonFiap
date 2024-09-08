# Projeto de TCC: Análise de Impacto da ONG Passos Mágicos

## Tema e Objetivo

O objetivo do projeto é desenvolver uma análise da base de dados fornecida pela ONG Passos Mágicos, que contém informações educacionais dos anos de 2020, 2021 e 2023. A proposta é demonstrar o impacto da ONG sobre a performance acadêmica dos estudantes atendidos, utilizando uma análise de dados exploratória com Python (Pandas, Numpy) e Power BI para visualização dos resultados. O foco principal será criar um _storytelling_ forte e emocional, apoiado em dados educacionais, que possa evidenciar o impacto positivo da ONG na comunidade atendida.

## Estrutura Esperada

O produto final incluirá:

- Um _dashboard_ interativo no Power BI que destacará os principais indicadores e resultados das análises.

- Um relatório técnico detalhado, apresentando a metodologia utilizada, os _insights_ gerados e a base teórica da análise.

# Etapas do Projeto

## 1. Exploração dos Dados
Nesta primeira etapa, o foco será obter uma compreensão profunda dos dados fornecidos pela ONG Passos Mágicos. A exploração inicial ajudará a identificar inconsistências, padrões e anomalias, além de possibilitar a preparação adequada para as análises futuras.

### 1.1. Limpeza de Dados

- **Objetivo:** Corrigir dados inconsistentes, lidar com valores ausentes e preparar a base para as próximas fases.

 - **Exemplo:** Se houver dados faltantes nas notas de alunos em determinados anos, será necessário decidir se esses dados serão removidos ou imputados.

 - **Ferramentas:** Pandas para tratamento e limpeza de dados.

 - **Código exemplo:**
    ```
    df.dropna(subset=['Notas'], inplace=True)  # Remove linhas com valores ausentes nas notas
    ```

### 1.2. Verificação de Consistência

- **Objetivo:** Verificar se as variáveis estão corretamente formatadas e se os dados seguem a lógica esperada.

  - **Exemplo:** Certificar-se de que os valores de frequência escolar estão entre 0 e 100%.

### 1.3. Transformação de Dados

- **Objetivo:** Modificar e preparar os dados para análise, como converter datas ou criar novas variáveis.
  - **Exemplo:** Criar uma nova coluna que agrupe os alunos por faixa etária.

## 2. Definição dos Indicadores

A segunda etapa envolve a definição dos principais indicadores (KPIs) que serão utilizados para medir o impacto da ONG Passos Mágicos. Esses KPIs serão centrais para as análises e a construção do _dashboard_.

### 2.1. Indicadores de Desempenho Acadêmico

- **Exemplo:** Notas médias em disciplinas como matemática e português, comparando os anos de 2020, 2021 e 2023.
- **Fórmula:** Média das notas por ano.
- **Código exemplo:**
  `df.groupby('Ano')['Nota_Matemática'].mean()`

### 2.2. Indicadores de Frequência Escolar

- **Exemplo:** Taxa média de frequência escolar por ano, utilizada para medir o envolvimento dos alunos no período analisado.
- **Fórmula:** Média da frequência escolar anual.

### 2.3. Indicadores de Retenção e Abandono Escolar

- **Exemplo:** Percentual de alunos que permaneceram ou abandonaram os estudos durante o período analisado.
- **Fórmula:** Percentual de alunos que foram retidos ou abandonaram os estudos em relação ao total de alunos por ano.

### 2.4. Indicadores de Engajamento em Programas Extracurriculares

- **Exemplo:** Percentual de alunos que participaram de atividades promovidas pela ONG e a relação com o desempenho acadêmico.

## 3. Análises e Modelagem

Esta etapa é focada em análises mais profundas para extrair _insights_ valiosos e, opcionalmente, construir modelos preditivos que ajudem a entender melhor os fatores que influenciam o sucesso dos alunos.

### 3.1. Análise Exploratória dos Dados (EDA)

- **Distribuição dos Dados:** Análise de cada variável de forma isolada (univariada), como as notas médias dos alunos em diferentes disciplinas.

  - **Exemplo: Visualizar a** distribuição das notas com histogramas.

  - **Código exemplo:**
    `sns.histplot(df['Nota_Matemática'], kde=True)`

- **Correlação entre Variáveis:** Identificar como diferentes variáveis estão relacionadas, como a frequência escolar e o desempenho acadêmico.

  - **Código exemplo:**
    `sns.heatmap(df.corr(), annot=True)`

- **Análise Temporal:** Comparar os dados ao longo dos anos, identificando tendências no desempenho dos alunos.

  - **Código exemplo:**
    `df.groupby('Ano')['Nota_Matemática'].mean().plot(kind='line')`

### 3.2. Definição de Métricas Estatísticas

- **Média e Mediana:** Avaliar o desempenho central dos alunos.

- **Desvio Padrão e Variância:** Analisar a dispersão dos dados.

  - **Código exemplo:**
    `df.groupby('Ano')['Nota_Matemática'].std()`

### 3.3. Análise de Impacto

- **Comparação Antes e Depois:** Comparar o desempenho acadêmico de alunos antes e depois da intervenção da ONG.

- **Código exemplo:**
  ```
  df['Delta_Notas'] = df['Nota_2023'] - df['Nota_2020']
  df['Delta_Notas'].mean()
  ```
- **Testes Estatísticos:** Validar a significância das mudanças observadas com testes de hipóteses.

  - **Código exemplo:**
  ```
    from scipy.stats import ttest_ind
    ttest_ind(df['Nota_2020'], df['Nota_2023'])
  ```

### 3.4. Modelagem Preditiva (Opcional)

Se houver interesse, você pode construir modelos de regressão ou classificação para prever o desempenho futuro ou identificar os fatores mais influentes.

- **Exemplo:** Regressão Linear para prever notas com base na frequência escolar.

- **Código exemplo:**
  ```
  from sklearn.linear_model import LinearRegression
  model = LinearRegression().fit(X, y)
  ```

## 4. _Storytelling_ e Power BI

Esta etapa envolve transformar os _insights_ obtidos nas análises em uma narrativa coesa e envolvente, utilizando o Power BI para visualização interativa dos dados.

### 4.1. _Storytelling_ com Dados

- **Definir a Mensagem Central:** A mensagem principal deve destacar o impacto positivo da ONG Passos Mágicos, como a melhora no desempenho escolar.

  - **Exemplo:** “A ONG contribuiu para um aumento de 20% nas notas de matemática entre 2020 e 2023.”

- **Estrutura Narrativa:** Siga uma estrutura de começo, meio e fim para guiar a apresentação dos dados.

  - **Exemplo:**
    - **Início:** Apresentação dos desafios educacionais antes da intervenção da ONG.
    - **Meio:** Demonstração das ações implementadas e seus efeitos.
    - **Fim:** Resultados obtidos e impactos positivos.

- **Humanizar os Dados:** Use exemplos de alunos ou grupos para tornar a narrativa mais envolvente.

  - **Exemplo:** Relatar a história de um estudante que melhorou suas notas graças ao programa de reforço.

### 4.2. Criação do _Dashboard_ no Power BI

- **Planejamento do _Dashboard_:** Defina os KPIs mais importantes para serem exibidos de forma clara e visualmente atraente.

  - **Exemplo:** Um gráfico de linha mostrando a evolução das notas ao longo dos anos.

- **Escolha de Visualizações:** Utilize gráficos de linha, barras, e mapas de calor para representar diferentes tipos de dados.

  - **Exemplo:** Um gráfico de barras para comparar a taxa de retenção entre 2020 e 2023.

- **Interatividade e Filtros:** Permita que o usuário explore os dados filtrando por categorias como ano ou disciplina.

- **_Layout_ e _Design_:** Organize o _dashboard_ de forma clara, com uma página inicial contendo os principais KPIs e outras páginas detalhando os _insights_.