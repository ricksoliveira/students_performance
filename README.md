O DataSet a ser analisado será o "Performance de estudantes", onde reúne alguns parâmetros de à classe social e notas em diferentes provas (matemática e português) de alunos reais de duas escolas brasileiras (Gabriel Pereira e Mousinho da Silveira), no ano de 2008.

O objetivo desta análise é entender melhor quais fatores podem contribuir mais para um determinado aluno conseguir ter um desempenho e aprendizado melhor, assim como poder prever, com um modelo simples, as notas mais prováveis de um aluno ter quando preenchendo alguns parâmetros.

Este DataSet foi retirado do website [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu), e pode ser acessado por este [LINK](https://archive.ics.uci.edu/dataset/320/student+performance).

### Sumário

>- 1.....................................................Importação dos DataSets.
>
>   - 1.1........................................Definição de Funções.
>    
>- 2.....................................................Dicionário de Colunas.
>
>- 3.....................................................Preparação dos Dados.
>
>- 4.....................................................Uma análise exploratória.
>
>   - 4.1........................................Algumas análises Univariadas.
>
>   - 4.2........................................Algumas análises Bivariadas.
>
>       - 4.2.1...........................Relações de Nota vs Algumas variáveis categóricas.
>
>       - 4.2.2...........................Correlações das Variáveis numéricas.
>
>       - 4.2.3...........................Comportamento das médias.
>
>- 5.....................................................Considerações finais.
>
>   - 5.1........................................Conclusões e hipóteses.
>
>   - 5.2........................................Propostas.

### Sumário de Imagens

> Gráfico 1...............................................Barras - Quantidade de cada gênero.
>
> Gráfico 2...............................................Histograma - Frequência de cada nota por trimestre.
>
> Gráfico 3...............................................Boxplot - Outliers de falta.
>
> Gráfico 4...............................................Violino - Frequência de Notas por tipo de endereço.
>
> Gráfico 5...............................................Violino - Frequência de Notas por tempo de deslocamento.
>
> Gráfico 6...............................................Violino - Frequência de Notas por suporte educacional.
>
> Gráfico 7...............................................Violino - Frequência de Notas por relação familiar.
>
> Gráfico 8...............................................Violino - Frequência de Notas por tamanho da família.
>
> Gráfico 9...............................................Mapa de Calor - Correlação das variáveis numéricas de Matemática.
>
> Gráfico 10............................................Mapa de Calor - Correlação das variáveis numéricas de Português.
>
> Gráfico 11............................................Linha - Tempo de Estudo por Média de nota.
>
> Gráfico 12............................................Barras e Linha - Quantidade de Cada educação de Pai/Mãe e Média de nota por Educação dos pais.

# 1 - Importação dos DataSets

##### Após fazer a importação dos datasets, podemos ver qual a cara dos dados, como estão escritas variáveis categóricas, se há caracteres especiais, assim como utilizar funções que nos dê uma idéia de dados faltantes.

##### No caso, podemos contar que estes datasets tem 1000 registros no total, e nenhum dos dados está nulo ou faltante, facilitando assim os próximos passos.

# 2 - Dicionário de Colunas

#### Para o melhor entendimento do que cada uma das categorias significa no contexto da análise, é necessário um dicionário de cada uma das colunas
1) **school**.......................................Escola ("GP" = Gabriel Pereira / "MS" = Mousinho da Silveira)

2) **sex**..............................................Genero ("F" = Feminino / "M" = Masculino)
3) **age**..............................................Idade do aluno
4) **address**.....................................Tipo do endereço ("U" = Urbano / "R" = Rural)
5) **famsize**.....................................Tamanho da Família ("LE3" = 3 Pessoas ou menos / "GT3" = Mais que 3 pessoas)
6) **Pstatus**......................................Estatus dos pais ("J" = Morando juntos / "S" = Separados)
7) **Medu**.........................................Educação da Mãe (0 = Nenhum / 1 = Fundamental / 2 = Quinto até Nono ano / 3 = Colégio / 4 = Ensino Superior)
8) **Fedu**...........................................Educação do Pai (0 = Nenhum / 1 = Fundamental / 2 = Quinto até Nono ano / 3 = Colégio / 4 = Ensino Superior)
9) **Mjob**..........................................Ocupação da Mãe (Professor / Saúde / Func. Público / Lar / Outro)
10) **Fjob**............................................Ocupação do Pai (Professor / Saúde / Func. Público / Lar / Outro)
11) **reason**.......................................Razão para escolher a escola ("Local" = Perto de casa / Reputação / "Curso" = Preferencia de curso / Outro)
12) **guardian**..................................Guarda do estudante
13) **traveltime**...............................Tempo de casa até a escola (1 = Menos que 15 min / 2 = 15 a 30 min / 3 = 30 min a 1 hora / 4 = Maior que 1 hora)
14) **studytime**................................Tempo semanal de estudo (1 = Menos que 2 horas / 2 = 2 a 5 horas / 3 = 5 a 10 horas / 4 = Mais que 10 horas)
15) **failures**......................................Número de vezes que o aluno repetiu de ano
16) **schoolsup**................................Teve suporte educacional extra (Sim ou Não)
17) **famsup**......................................Teve suporte educacional familiar (Sim ou Não)
18) **paid**.............................................Teve aulas extras pagas dentro da disciplina do curso (Matemática ou Português) (Sim ou Não)
19) **activities**...................................Teve atividades extracurriculares (Sim ou Não)
20) **nursery**......................................Frequentou creche (Sim ou Não)
21) **higher**.........................................Deseja cursar ensino superior (Sim ou Não)
22) **internet**.....................................Tem acesso à internet em casa (Sim ou Não)
23) **romantic**...................................Está em um relacionamento amoroso (Sim ou Não)
24) **famrel**........................................Qualidade das relações familiares (De 1 = Muito ruim até 5 = Excelente)
25) **freetime**....................................Tem tempo extra depois da escola (De 1 = Muito baixo até 5 = Muito alto)
26) **goout**.........................................Sai com os amigos (De 1 = Muito baixo até 5 = Muito alto)
27) **Dalc**.............................................Consumo de álcool durante a semana (De 1 = Muito baixo até 5 = Muito alto)
28) **Walc**............................................Consumo de álcool no final de semana (De 1 = Muito baixo até 5 = Muito alto)
29) **health**.........................................Estado de saúde atual (De 1 = Muito baixo até 5 = Muito alto)
30) **absences**...................................Número de faltas na escola
31) **G1**................................................Nota do primeiro trimestre (De 0 a 20)
31) **G2**................................................Nota do segundo trimestre (De 0 a 20)
32) **G3**................................................Nota final (terceiro trimestre) (De 0 a 20)

# 3 - Preparação dos dados

##### Não sendo necessário fazer nenmhum tratamento referente à dados faltantes, podemos tratar as variáveis categóricas

##### Vamos realizar algumas preparações, como abreviações, traduções, mudanças que não causarão impacto à integridade dos dados, a fim de apenas facilitar o entendimento.

# 4 - Uma análise exploratória

### 4.1 - Algumas análises Univariadas

##### Iniciaremos a análise vendo algumas variáveis separadamente, como estes dados mostram notas de provas de alunos, as três perguntas iniciais que queremos fazer são:

1) Qual a proporção de homens e mulheres ?
2) Quantas vezes cada nota foi obtida ?
3) Há alguma variável da qual devemos nos preocupar com *outliers*, ou seja, valores muito fora da curva ?

##### Podemos alcançar as respostas das 2 primeiras perguntas com gráficos de barra simples e histogramas. Já a terceira pergunta, baseado no dicionário das variáveis, como a maioria estão numa escala de 1 a 5, não haverão valores fugindo disto, apenas a variável *"absences"* (número de faltas) poderá nos mostrar algum valor discrepante, para ela, usaremos um gráfico de boxplot.
##### Os gráficos de barra abaixo mostram que para matemática, a quantidade de homens e mulheres são bem parecidas, porém em português, uma quantidade um pouco maior de dados de alunas foi coletado.

> ![51f3ef6c-97af-444f-aab0-ff1181d333bb](https://github.com/user-attachments/assets/14863eea-8e82-454c-8070-49491d5f2f1a)
> 
> Gráfico 1 - Barras - Quantidade de cada gênero.

##### Os 6 histogramas abaixo representam a frequência de cada nota, cada linha representa uma matéria, e cada coluna um trimestre do ano.

> ![1de12f98-58f8-4359-9d19-40efbae62ef2](https://github.com/user-attachments/assets/05d1e91a-ff04-4e65-87f7-cc3e9d17da51)
>
> Gráfico 2 - Histograma - Frequência de cada nota por trimestre.

##### Podemos concluir que, a quantidade de notas baixas aumentam com o passar do ano para ambas as matérias, porém este aumento é muito mais evidente em matemática. Da qual do 2º para o 3º trimestre, o número de alunos que tiraram nota 0 quase triplicaram.

#### Este aumento significativo em matemática mas não tanto em português, pode ser causado pelos aumento da dificuldade da matéria, ou talvez a metodologia adotada pela escola. Outra análise poderá concluir algo correlacionando isso com alguma outra variável disponível.
#### Abaixo temos um gráfico boxplot da quantidade de faltas dos alunos, com o objetivo de analisar outliers.

> ![cc084d3d-bbba-4afe-9733-d8420321c1fe](https://github.com/user-attachments/assets/3022979c-446c-4192-b89d-12e79a7f9a4f)
>
> Gráfico 3 - Boxplot - Outliers de falta.

#### Podemos tirar duas principais conclusões com os gráficos acima:

1) Alunos faltaram quase duas vezes mais às aulas de matemática do que português.
2) Os alunos que tiveram uma falta muito acima da média, faltaram mais do que o dobro em matemática do que português, ou seja, emquanto temos 2 alunos que faltaram 30 ou 35 vezes me português, temos 5 alunos que faltaram mais de 35, 40, mais de 50 e até mais do que 70 vezes.

#### Essas duas conclusões podem nos ajudar a entender o decaimento das notas de matemática, que embora tanto a nota quanto falta possam consequências de uma outra causa em comum, as faltas tem uma grande chance de ser um fator contribuinte para o decaimento das notas.
## 4.2 - Algumas análises Bivariadas
### 4.2.1 - Relações de Nota vs Algumas variáveis categóricas

##### Tendo uma ideia inicial de como as variáveis se comportam e hipotetizando algumas possíveis causas pra esses comportamentos, vejamos como algumas dessas variáveis se comportam com relação à outras.

##### Para isso, podemos pensar em algumas perguntas iniciais simples, que envolvam a nota e alguma variável categórica e não numérica:

1) Será que há uma diferença entre notas dependendo de onde o aluno mora ?
2) Será que há uma diferença entre notas dependendo de se o aluno teve algum suporte ou aula extra ?
3) Será que há uma diferença entre notas dependendo do tamanho e relação familiar dos alunos ?

##### Vamos alinsar algumas dessas questões utilizando gráficos de sino.

> ![138b9cf8-bbab-4940-9bd0-562d87fbce89](https://github.com/user-attachments/assets/285eb89f-b800-477f-a65d-e6bf266c8036)
>
> Gráfico 4 - Violino - Frequência de Notas por tipo de endereço.

<br><br>

> ![46609510-b218-47fc-8729-38ae764630e9](https://github.com/user-attachments/assets/5516b08e-1ed6-40f5-94f1-b0510e1640fe)
>
> Gráfico 5 - Violino - Frequência de Notas por tempo de deslocamento.
> 
> 1 - Menos de 15 minutos
> 
> 2 - 15 a 30 Minutos
> 
> 3 - 30 a 60 minutos
> 
> 4 - Mais de 60 minutos

<br><br>

> ![b8f9995e-a09b-4ee8-bacb-ba6a842c819b](https://github.com/user-attachments/assets/5b85b7a6-e4d9-4140-b75b-eedfd7901023)
>
> Gráfico 6 - Violino - Frequência de Notas por suporte educacional.

<br><br>

> ![1f5b6de4-8043-4398-82f6-ff5f4e0f91bf](https://github.com/user-attachments/assets/ec06cf90-27f7-4eec-be67-1425517bf618)
>
> Gráfico 7 - Violino - Frequência de Notas por relação familiar.
>
> 1 - Muito ruim
>
> 2 - Ruim
>
> 3 - Normal
>
> 4 - Boa
>
> 5 - Excelente

<br><br>

> ![83718c38-b761-4f51-8e2a-251cb5ebd93c](https://github.com/user-attachments/assets/cb6d42fa-006c-4c84-99a3-6ef4f953c4c8)
>
> Gráfico 8 - Violino - Frequência de Notas por tamanho da família.
>
> LE3 - Menor ou igual a 3 integrantes
>
> GT3 - Mais que 3 integrantes

##### Os gráficos acima nos permitem tirar algumas conclusões:

1) Confirmação de que as notas, em todos os casos, diminuem ao longo do ano, principalmente em matemática.
2) Alunos que moram em zona urbana tendem a ter uma concentração maior de notas acima da média e uma concentração menor de notas baixas *(Gráfico 4)*.
3) Alunos que levam mais tempo se deslocando de casa para a escola tendem a ter notas menores *(Gráfico 5)*.
4) Alunos com suporte educacional extra tendem a concentrar suas notas entre 7.5 e 10, enquanto alunos sem suporte tem uma frequencia de notas mais distribuidas. Porém apenas no começo do ano, do meio para frente, há um aumento de notas baixas e 0 para os alunos sem suporte *(Gráfico 6)*.
5) A relação familiar do aluno interfere muito pouco para as suas notas, alunos com uma boa relação familiar até demonstram ter uma frequência de notas baixas um pouco maior do que alunos com uma má relação familiar *(Gráfico 7)*.
6) Alunos com família maior de 3 pessoas tem uma maior concentração te notas baixas do que alunos com família menor *(Gráfico 8)*.
### 4.2.2 - Correlações das Variáveis numéricas

##### Vimos algumas relações das notas com variáveis categóricas, como as notas se relacionam com variáveis numéricas ? Posto isso, há perguntas que são importantes fazermos, por exemplo:

1) Qual a correlação da nota com a educação dos pais ?
2) Qual a correlação da nota com o numero de faltas ou repetições de ano ?
3) Há uma correlação forte entre outras variáveis sem ser nota ? Essa correlação pode explicar alguma das hipóteses estipuladas até agora ?

##### Fazemos isso calculando a correlação entre uma variável e outra, e gerando um número, variando de -1 a 1.

##### Estes números são então colocados em uma matriz, e cada número é pintado de uma cor diferente, onde é possível saber qual variável se relaciona com qual, e se a correlação é forte ou fraca.

##### ***OBS: O número da correlação, quanto mais próximo de 1, significa uma correlação positiva forte, ou seja são diretamente proporcionais, conforme uma variável sobe, a outra também sobe. Quanto mais próximo de -1, significa uma correlação negativa forte, ou seja inversamente proporcionais, conforme uma variável sobe, a outra desce. E quanto mais próximo de 0, significa que há muito pouca ou nenhuma correlação entre as variáveis.***

> ![e82b2c6f-f43b-4b00-b3b2-99c8180662ba](https://github.com/user-attachments/assets/464e1159-6705-428b-94cf-3c0b52f659d6)
>
> Gráfico 9 - Mapa de Calor - Correlação das variáveis numéricas de Matemática.

<br><br>

> ![5093e524-b083-41d8-bab3-ea2098355e13](https://github.com/user-attachments/assets/5ba210d2-a86e-4478-8454-1fa78e6e7b77)
>
> Gráfico 10 - Mapa de Calor - Correlação das variáveis numéricas de Português.

##### Com os mapas de calor acima, vemos alguns pontos interessantes:

1) Há uma correlação positiva entre a educação dos pais e as notas (entre 0.15 e 0.26).
2) Há uma correlação negativa entre a educação dos pais e o tempo que um aluno leva para chegar à escola (entre -0.27 a -0.16).
3) Há uma correlação positiva forte entre as notas, alunos que tiraram notas boas em um trimestre dificilmente tiram notas ruins em outro (entre 0.8 e 0.92).
4) *Confirmamos que quase não há correlação entre notas e relação familiar dos alunos, já que a relação familiar também não está correlacionado com quanto tempo o aluno estuda*.


##### Sobre consumo de álcool

*Há uma correlação negativa entre consumo de alcool e as notas, porém quase não há correlação entre nota e quantas vezes o aluno sai com os amigos para as notas em Português. Esta relação se inverte para as notas de Matemática, da qual quase não há correlação entre consumo de alcool e notas, porém há correlação negativa entre nota e quantas vezes o aluno sai*.

##### Sobre tempo de estudo

*Há uma correlação entre quanto tempo o aluno passa estudando e sua nota, ou seja, quanto mais tempo um aluno passa estudando, maior é a nota. Porém, essa correlação é quase o dobro em Português do que em Matemática. Podendo explicar o maior aumento de notas baixas durante o ano, significando que esta matéria fique bastante difícil com relação ao tempo, de maneira que nem um aluno que passa muito tempo estudando consiga um bom desempenho.*
### 4.2.3 - Comportamento das médias

##### Com as observações vistas anteriormente, vamos colocar em alguns gráficos e tabelas, o comportamento da média das notas em relação à quanto tempo o aluno estuda e à educação dos pais.

> ![be6d61e1-449e-4dd1-97ad-8d4b06afc4c2](https://github.com/user-attachments/assets/6ef5a002-d898-46b9-9311-912e3d9bff8a)
>
> Gráfico 11 - Linha - Tempo de Estudo por Média de nota.

##### O gráfico acima nos mostra que há um aumento na nota dos alunos que gastam mais tempo estudando, porém há comumente um decréscimo nas notas dos alunos que estudam mais de 10 horas.

##### *Isso explica a diminuição na correlação, porém, com estes dados, não é possível pontuar com exatidão a causa para o fato dos alunos que mais estudam, diminuirem as notas.*
##### Analisemos agora as notas com relação ao nivel educacional dos pais. Abaixo uma tabela com a média das notas de Matemática para cada nível de educação do Pai.

> | Escolaridade do Pai | Média 1º Tri | Média 2º Tri | Média 3º Tri |
> | ----------------    | ---------    | ---------    | ---------    |
> | Sem escolaridade    | 12.00        | 13.00        | 13.00        |
> | Ensino Fundamental  | 9.73         | 9.39         | 9.16         |
> | Ginásio             | 11.03        | 10.88        | 10.26        |
> | Colégio             | 10.74        | 10.75        | 10.66        |
> | Ensino Superior     | 11.93        | 11.56        | 11.36        |

##### Esta tabela nos mostra que conforme o nível educacional dos pais sobe, a nota média dos alunos aumenta um pouco, porém, há um ponto interessante, vemos que a maior média é justamente obtida por alunos cujo os pais não tem nenhuma escolaridade, por que isso ocorre ?

##### Como a média é um número exato, podemos supor que há apenas 2 ou 1 alunos nesta condição, logo, com uma amostra pequena, irregularidades podem ocorrer, vamos plotar isso em uns gráficos, porém não só de matemática e educação do pai, mas sim todos:

> ![82eec06b-650b-4137-9d09-44ea5841e4f9](https://github.com/user-attachments/assets/379b46e4-d79e-46b3-aca3-bea46b7c6ac6)
>
> Gráfico 12 - Barras e Linha - Quantidade de Cada educação de Pai/Mãe e Média de nota por Educação dos pais.

##### Os gráficos acima corroboram a informação de que uma amostra pequena está elevando a média. Apenas entre 3 e 7 alunos tem pais sem nenhuma escolaridade. Estes pouco alunos coincidentemente tiraram uma nota mais alta, o que fizeram elevar a nota média deste grupo, explicando essa anormalidade.

##### É similar aos casos onde apenas 1 salário de um diretor ou presidente de empresa eleva a média salarial da empresa para um patamar muito alto, não condizente com o salário da grande maioria dos funcionários.

##### Tirando isso, há uma consistência nos dados, em que quanto maior o nível educacional de um pai ou mãe, em média um pouco maior será a nota dos filhos, as notas dos 3 trimestres crescem de maneira quase uniforme, não tendo nenhuma discrepância entre elas.
# 5 - Considerações finais.

### 5.1 - Conclusões e hipóteses.

##### Ao final de tudo, podemos concluir que as notas dos alunos decaem ao longo do ano, este decaimento é mais evidente em Matemática

Isso explica a diminuição na correlação, porém, com estes dados, não é possível pontuar com exatidão a causa para o fato dos alunos que mais estudam, diminuirem as notas.

Como o alcool influencia negativamente nas notas de português, mas não tanto em matemática, o alcool está correlacionado à quanto tempo livre e quantas vezes o aluno sai, e quando somamos ao fato de que, para português, quanto mais tempo um aluno estuda maior a sua nota, porém o tempo de estudo não impacta tanto na nota de matemática.

Tudo isso nos leva a crer que, há um menor tempo de dedicação aos estudos em matemática, e também há uma crescente complexidade na matéria ao longo do ano.
### 5.2 - Propostas.

##### A escola pode implementar a seguinte medida para combater estes problemas:

1) Aumentar interesse do aluno
2) Recompensar esforço

##### Aumentar o interesse do aluno em estudar matemática ao diminuir o foco em decorar fórmulas onde isso ocorre, ao invés, trazer problemas do ambiente do aluno para a sala de aula, mostrando onde tais numeros, fórmulas e metodologias se aplicam ao cotidiano do contexto em que o aluno está inserido, fazendo-o perceber como a matemática se aplica ao seu próprio dia a dia.

##### Recompensar o esforço do aluno, diminuindo um pouco a quantidade e complexidade do conteúdo, ao decorar menos fórmulas e entender mais, o aluno se sente mais recompensado, e consequentemente mais motivado à estudar mais, quando vê que seu entendimento foi convertido em uma nota maior.
