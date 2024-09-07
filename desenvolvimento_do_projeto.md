# Detalhamento da Metodologia de Desenvolvimento

## 1. Exploração dos Dados:

- Verificar a qualidade dos dados: Limpeza de dados, tratamento de valores ausentes, duplicados, etc.
- Identificar variáveis-chave que irão compor o storytelling.

A primeira etapa, Exploração dos Dados, é fundamental para garantir que seja possível entender dados que serão trabalhados e estejam prontos para serem analisados.

### 1. Entendimento Inicial dos Dados

- [ ] **Carregar e visualizar os dados:** Primeiro, importe a base de dados e obtenha uma visão geral. Isso pode ser feito carregando os dados com bibliotecas como `Pandas` e utilizando funções como `head()`, `info()`, e d`escribe()`.

- [ ] **Verificação da estrutura dos dados:** Verifique as colunas, tipos de dados (numérico, categórico, etc.) e a quantidade de registros.
        - **Exemplo:** `df.head()` para visualizar as primeiras linhas e `df.info()` para checar os tipos de dados e possíveis valores nulos.

- [ ] **Entendimento do contexto dos dados:** Tenha clareza sobre o significado de cada coluna e sua relação com os objetivos da ONG. Quais são as variáveis mais relevantes para medir o impacto?

### 2. Tratamento de Valores Ausentes

- [ ] **Identificação de valores ausentes:** Determine quais colunas têm valores ausentes e em que proporção.
    - **Exemplo:** `df.isnull().sum()` vai te mostrar quantos valores nulos existem por coluna.

- [ ] **Decisão sobre o tratamento:** Dependendo da quantidade de valores ausentes, você pode optar por:
    - Remover linhas ou colunas com muitos valores ausentes (se os dados faltantes forem significativos).
    - Preencher (imputar) valores ausentes com a média, mediana, ou outros métodos.
    - **Exemplo:** `df.fillna(df.mean())` para preencher valores ausentes com a média.


### 3. Tratamento de Dados Duplicados

- [ ] I**dentificação de duplicatas:** Verifique se há registros duplicados.
    - **Exemplo:** `df.duplicated()` mostra as linhas duplicadas.

- [ ] **Remoção de duplicatas:** Se encontrado, decida se essas duplicatas podem ser removidas.
    - **Exemplo:** `df.drop_duplicates()` para remover duplicatas.

### 4. Verificação de Outliers (Valores Atípicos)

- [ ] **Identificação de outliers:** Usar gráficos como boxplots ou análises estatísticas para encontrar valores fora do padrão.
    - **Exemplo:** `sns.boxplot(df['coluna'])` com seaborn para visualizar outliers.

- [ ] **Decisão sobre tratamento de outliers:** Dependendo do contexto, outliers podem ser removidos, transformados ou mantidos se forem relevantes.

### 5. Transformação de Dados (se necessário)

- [ ] **Conversão de tipos de dados:** Pode ser necessário converter tipos de dados, por exemplo, transformar colunas de datas em objetos de datetime.
    - **Exemplo:** `df['data']` = `pd.to_datetime(df['data'])`.

- [ ] **Normalização ou padronização de dados numéricos:** Se necessário para modelos ou visualizações mais claras.
    - **Exemplo:** Normalizar colunas com MinMaxScaler do sklearn ou usar uma transformação de log para reduzir a variabilidade.

### 6. Exploração Estatística Básica

- [ ] **Estatísticas descritivas:** Use métodos como `describe()` para gerar estatísticas como média, mediana, e desvio padrão, a fim de entender a distribuição dos dados.
    - **Exemplo:** `df.describe()` fornece uma visão geral de como os dados estão distribuídos.

- [ ] **Distribuição dos dados:** Use gráficos como histograma ou gráfico de dispersão para identificar padrões e distribuições.
    - **Exemplo:** `df['coluna'].plot(kind='hist')` ou `sns.pairplot(df)` para ver a relação entre as variáveis.

### 7. Documentação

Documentar todas as decisões tomadas: É importante manter um registro detalhado do que foi feito durante o processo de limpeza e exploração para que você possa justificar suas escolhas na etapa de relatório técnico.

## 2. Definição dos Indicadores:

- Estabelecer os principais KPIs que demonstram o impacto da ONG (ex: desempenho acadêmico antes e depois da intervenção, taxa de conclusão escolar, etc.).

A segunda etapa, Definição dos Indicadores, é crucial para medir o impacto da ONG Passos Mágicos. Os indicadores são métricas específicas que vão mostrar como os esforços da ONG estão influenciando os resultados educacionais da comunidade atendida. Aqui estão os detalhes:

### 1. Identificação dos Objetivos da ONG**

- [ ] **Compreender a missão da ONG:** Entenda claramente os principais objetivos da ONG Passos Mágicos no contexto educacional. Quais são as áreas de impacto que eles pretendem medir? Isso pode incluir melhorias no desempenho acadêmico, aumento da taxa de retenção escolar, ou desenvolvimento de habilidades socioemocionais.
 - **Exemplo de Objetivo:** Aumentar o desempenho acadêmico dos estudantes em áreas como matemática e leitura.

### 2. Escolha dos Indicadores Chave de Desempenho (KPIs)

- [ ] **Seleção dos KPIs mais relevantes:** Definir os indicadores que serão usados para medir os objetivos identificados. Esses KPIs precisam ser mensuráveis e estar disponíveis na base de dados.
    - **Exemplos de Indicadores:**

        - **Desempenho Acadêmico:** Média de notas em matérias como matemática, português, ciências.
        - **Evolução de Notas:** Comparação do desempenho dos alunos entre 2020, 2021 e 2023.
        - **Taxa de Retenção Escolar:** Percentual de alunos que continuam estudando no ano seguinte.
        - **Taxa de Conclusão Escolar:** Percentual de alunos que completam o ciclo educacional atendido pela ONG.
        - **Frequência Escolar:** Número médio de faltas por aluno, como indicador de engajamento.
        - **Participação em Atividades Extracurriculares:** Quantidade de alunos envolvidos em atividades complementares oferecidas pela ONG.
        - **Habilidades Socioemocionais:** Se houver dados, indicadores sobre a evolução de habilidades como resiliência, trabalho em equipe e comunicação.

### 3. Estratégias para Medir os Indicadores

- [ ] **Cálculo de métricas:** Definir como os indicadores serão medidos. Isso pode envolver cálculos diretos (como a média de notas) ou mais complexos (como a variação percentual de desempenho ao longo do tempo).
    - **Exemplo de Métrica:**
        - M**édia de Notas:** `(Nota_Matemática + Nota_Português + Nota_Ciências) / 3`.
        - **Variação Percentual do Desempenho:** `((Nota2023 - Nota2020) / Nota2020) * 100` para medir o percentual de melhora ou piora.
        - **Taxa de Retenção Escolar:** `Número de alunos em 2021 / Número de alunos em 2020 * 100`.

### 4. Comparação de Anos (2020, 2021, 2023)

- [ ] **Análise temporal:** Como a base de dados abrange três anos distintos, os indicadores devem ser medidos e comparados ao longo desse período. Isso vai permitir identificar tendências e mudanças no impacto da ONG.

- [ ] **Exemplo:** Comparar o desempenho médio dos alunos em 2020, 2021 e 2023 para ver se há uma tendência de melhora ou piora nos resultados.

### 5. Segmentação dos Dados

Agrupamento dos indicadores por subgrupos: Segmentar os indicadores por variáveis como idade, gênero, localização, ou outros fatores disponíveis no dataset. Isso pode revelar insights mais profundos, como se o impacto da ONG é maior em certos grupos.
Exemplo: Comparar o desempenho de meninos e meninas, ou de alunos de diferentes faixas etárias.

### 6. Verificação da Disponibilidade dos Dados

Checar a presença dos dados necessários: Antes de se comprometer com os KPIs, verifique se a base de dados contém as informações suficientes para calcular esses indicadores.
Exemplo: Verifique se a base tem colunas para as notas em matérias específicas, para a frequência escolar, etc.

### 7. Definição de Metas

Estabelecimento de metas: Defina metas claras para cada indicador, com base no que a ONG espera alcançar. Isso vai ajudar na comparação dos resultados obtidos com os resultados desejados.
Exemplo: A ONG pode ter como meta aumentar a média de notas em 15% ao longo de três anos ou reduzir a taxa de abandono escolar em 10%.

### 8. Validação dos Indicadores

Feedback com a ONG: Validar esses indicadores junto à ONG Passos Mágicos para garantir que eles realmente representam o impacto desejado. Certifique-se de que as métricas escolhidas estão alinhadas com as expectativas da ONG.

### 9. Documentação dos Indicadores

Documentar todos os KPIs escolhidos: Registrar todas as métricas que serão analisadas, a fórmula de cálculo de cada uma, e o motivo pelo qual foram selecionadas.
Exemplo: KPI: Média de notas, Fórmula: Soma das notas nas disciplinas principais dividida pelo número de disciplinas, Justificativa: Mede diretamente o desempenho acadêmico dos estudantes.

Com esses indicadores bem definidos, você estará pronto para iniciar a análise dos dados e mensurar o impacto da ONG de forma objetiva e clara. Eles serão a base tanto para o storytelling quanto para o dashboard no Power BI.

## 3. Análises e Modelagem:

- Aplicar a análise exploratória (distribuições, correlações, outliers).
- Gerar insights que suportem o storytelling, como evolução dos indicadores ao longo dos anos.



## 4. Storytelling e Power BI:

- Organizar os resultados em uma narrativa que conecte dados com impacto emocional.
- Criar o dashboard no Power BI que seja interativo e fácil de interpretar.