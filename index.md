---
title: Introdução aos programas do conjunto BLUPF90
author: Daniele Alves de Oliveira
date: Setembro 2025
subject: "Introdução aos programas do conjunto BLUPF90"
tags: [introdução,tutorial]
...

# Introdução

## Breve introdução aos programas BLUPF90

### O que é BLUPF90?

BLUPF90 é o nome do software. É também o nome de uma coleção de programas derivados do BLUPF90. Neste último caso, nos referiremos a ele como família BLUPF90 ou programas BLUPF90. Uma descrição concisa também pode ser encontrada no wiki oficial da Universidade da Geórgia (<http://nce.ads.uga.edu/wiki/doku.php>).
A família de programas BLUPF90 é uma coleção de softwares em Fortran 90/95 para cálculos de modelos mistos em melhoramento animal. O objetivo do software é ser tão simples quanto um pacote matricial e tão eficiente quanto uma linguagem de programação.
O programa BLUPF90 cria e resolve equações de modelos mistos. Ele suporta vários modelos, incluindo o modelo animal, o modelo materno e o modelo de regressão aleatória com múltiplas características. O conjunto de programas está disponível no site oficial (<http://nce.ads.uga.edu>) e pode ser usado gratuitamente para fins acadêmicos ou de pesquisa.

### Por que o BLUPF90?

O BLUPF90 oferece diversas vantagens em relação a softwares similares para os usuários: simplicidade, estabilidade e desenvolvimento ativo.
Para programadores, a estrutura interna é documentada em uma nota do curso (<https://nce.ads.uga.edu/wiki/doku.php?id=courses>) e o código-fonte funcional está disponível, permitindo que um desenvolvedor modifique o programa para suportar novas ideias.
Agora, analisaremos suas vantagens do ponto de vista do usuário.

#### Simplicidade

O comportamento do programa é muito simples. Cada programa BLUPF90 lê um arquivo de parâmetros, que descreve os nomes dos arquivos de dados e de linhagem, modelos e componentes de variância (iniciais) a serem usados ​​na análise.
O arquivo de parâmetros é um pequeno arquivo de texto contendo alguns pares de palavras-chave e valores para descrever as informações. É conciso, mas capaz de especificar modelos gerais. Depois de aprender a escrever um arquivo de parâmetros, você poderá realizar análises muito complexas com o programa.
Cada programa salva as soluções das equações do modelo misto (por exemplo, EBV) em um arquivo. Os componentes de variância estimada também são salvos em arquivos permanentemente.

#### Estabilidade

Os programas foram testados por muitos pesquisadores desde seu lançamento público por volta de 2000. Eles agora são estáveis ​​o suficiente para serem usados ​​em avaliações genéticas de rotina em nível nacional. A equipe da Universidade da Geórgia utiliza intensamente os programas em suas pesquisas.

### É fácil?

Sim, é. Entretanto, o processo de aprendizagem nem sempre é simples. Podem surgir vários obstáculos ao se aprender a usar os programas BLUPF90 em pesquisas reais. Este é o outro lado da moeda da sua aparente simplicidade.

**Documentação limitada:**
O site oficial hospeda um manual para os programas (<http://nce.ads.uga.edu/wiki/doku.php>), que contém diversas informações sobre o software.
No entanto, a documentação disponível, especialmente para iniciantes, ainda é restrita e pode não cobrir todos os detalhes necessários.

**Manipulação de dados:**
Essa não é uma limitação exclusiva do BLUPF90, mas um desafio comum a softwares de análises genéticas.
A família BLUPF90 é voltada para modelos mistos, sem oferecer recursos internos de manipulação de dados como o R ou o SAS.
Como os programas utilizam arquivos de texto como entrada, é necessário preparar previamente os arquivos de dados e de pedigree, garantindo que estejam no formato exigido e sem registros inconsistentes.

**Pré-processamento:**
Todos os programas aceitam apenas valores numéricos, para manter a programação simples.
Se seus arquivos de dados ou pedigree contiverem caracteres (letras ou símbolos), eles devem ser substituídos por códigos inteiros antes da análise.
Um dos programas, o RENUMF90, pode executar essa tarefa. Para dados de campo ou comerciais, é indispensável rodar o RENUMF90 antes de utilizar o BLUPF90.

### Diferenças gerais

**R e SAS**

**Capacidade e velocidade:**
O BLUPF90 é capaz de lidar com conjuntos de dados muito grandes e, em geral, é mais rápido que o R e o SAS para esse tipo de análise.

**Modo de operação:**
O BLUPF90 não é interativo. O usuário precisa preparar um arquivo de parâmetros contendo todos os detalhes da análise (nomes dos arquivos, modelo, parâmetros genéticos e opções).
O programa apenas lê o arquivo e executa a tarefa definida.

**Sem linguagem de script:**
Diferentemente do R ou do SAS, o BLUPF90 não possui funções para manipulação de dados.
Toda a edição ou pré-processamento deve ser feito antes da execução.
O arquivo de dados já deve conter todas as informações necessárias para a análise.

**Formato dos arquivos:**
O BLUPF90 lê apenas arquivos de texto.
Não são permitidos cabeçalhos (*headers*) nem comentários nos arquivos de dados ou pedigree.
Os itens em cada linha devem ser separados por um ou mais espaços.

**Saída de resultados:**
Os resultados são exibidos na tela e também gravados em arquivos de texto.

**Valores aceitos:**
O programa aceita apenas:

+ valores inteiros para níveis de efeitos (ex.: identificadores de animais, grupos, categorias);

+ valores reais para covariáveis e características (*traits*).
Letras ou símbolos devem ser convertidos em códigos numéricos antes da análise.
O programa RENUMF90 pode auxiliar nessa conversão.

**Interface:**
O BLUPF90 não possui interface gráfica. Seu funcionamento é semelhante ao Rscript:

+ é executado via linha de comando (Prompt de Comando/DOS no Windows, Terminal no macOS ou shells no Linux).

**Testes de hipótese:**
O BLUPF90 não fornece funções próprias para testes de hipótese.
Alguns programas da família apresentam estatísticas como −2logL, que podem ser usadas pelo usuário para realizar manualmente testes de razão de verossimilhança (LRT).

**Recursos atuais:**
Os programas mais recentes dão suporte a análises genômicas, especialmente para GBLUP de etapa única (*Single-Step GBLUP*).
O tempo de processamento foi significativamente aprimorado em procedimentos como:

+ REML (Máxima Verossimilhança Restrita),
+ BLUP com iteração nos dados, graças ao uso de paralelização e bibliotecas otimizadas.

## Atualização para os programas BLUPF90+

Desde 2022, os programas da família BLUPF90 passaram por uma reorganização e alguns deles foram unificados em uma versão mais moderna. As principais diferenças entre os programas antigos e os atualizados foram descritas por Lourenco et al. (2022) nos anais do WCGALP.

O principal destaque é a criação do BLUPF90+, que integra em um único executável as funções antes distribuídas entre os programas blupf90, remlf90 e airemlf90. Por padrão, o BLUPF90+ opera da mesma forma que o antigo blupf90, construindo e resolvendo o sistema de equações de modelos mistos a partir dos dados e dos componentes de variância especificados no arquivo de parâmetros fornecido pelo usuário. Além disso, o BLUPF90+ permite estimar componentes de variância por REML, utilizando a opção *OPTION method VCE* no arquivo de parâmetros, e possibilita a escolha do algoritmo de estimação. O algoritmo padrão é o AI (*Average Information*), mas o usuário pode alternar para EM (*Expectation–Maximization*) por meio da opção *OPTION EM-REML*.

## Como Executar programas de linha de comando

Se você não tem experiência em rodar programas pela linha de comando...

Executar um programa pela linha de comando é, na verdade, uma dúvida bastante comum. O método padrão é usar o **Prompt de Comando** (ou simplesmente **cmd**), que é um console onde você digita comandos pelo teclado.

Também é possível utilizar o **PowerShell** em vez do Prompt de Comando; o procedimento é o mesmo.

Existem muitos tutoriais disponíveis sobre esse assunto, por exemplo:

+ Prompt de Comando – Como usar comandos básicos
(<http://www.digitalcitizen.life/command-prompt-how-use-basic-commands>)

+ Como usar a linha de comando do Windows (DOS)
(<http://www.computerhope.com/issues/chusedos.htm>)

+ Como executar um arquivo a partir do MS-DOS?
(<http://www.computerhope.com/issues/ch000598.htm>)

+ Guia para iniciantes: Prompt de Comando do Windows
(<http://www.pcstats.com/articleview.cfm?articleID=1723>)

+ Como abrir o Prompt de Comando
(<http://pcsupport.about.com/od/commandlinereference/f/open-command-prompt.htm>)

## Como executar o programa

O procedimento básico para rodar o programa é o seguinte:

1. Baixe o programa e salve-o em uma pasta.

2. Salve os arquivos necessários na mesma pasta.

3. Abra o Prompt de Comando e use o comando cd para mudar para o diretório da pasta onde o programa foi salvo.

4. Digite o nome do programa (por exemplo, `blupf90+` ou `blupf90+.exe`) para executá-lo.

5. Quando solicitado, digite o nome do arquivo de parâmetros. Alguns programas podem pedir informações adicionais.

6. Aguarde a análise ser concluída.

7. Confira e colete os resultados.

# Blup, ssBlup, Metafundadores (MFs), Grupos Parentais Desconhecidos (UPGs) e Truncamento de Pedigree — Análises com dados

**Objetivo:** Ensinar passo a passo como simular dados (pedigree, genótipos e fenótipos) e ajustar modelos de avaliação genética utilizando diferentes estratégias:

+ BLUP tradicional;

+ ssGBLUP;

+ Modelos com UPGs;

+ Modelos com Metafundadores (MFs);

+ Modelos com truncamento de pedigree.

**Pré-requisitos:** R (>=4.x), BLUPF90+ (inclui RENUMF90), utilitários de terminal (Linux/macOS/Windows), conhecimentos básicos de linha de comando.

## Sobre este tutorial

### Informações gerais

Este material foi elaborado para orientar a configuração de modelos em arquivos de parâmetro e a preparação de arquivos de dados, pedigree e genótipos utilizados nos programas da família BLUPF90, com foco em análises genômicas aplicadas à avaliação genética de bovinos de corte.
O tutorial assume que o leitor já possua conhecimento básico de modelos lineares mistos e noções de manipulação de dados em computador. Experiência prévia com softwares de análise genética, como BLUPF90 ou similares, também é desejável para melhor compreensão.

As funcionalidades do BLUPF90+ são apresentadas de forma progressiva. Cada capítulo inicia com exemplos simples e didáticos, seguidos de aplicações mais práticas que envolvem metafundadores (MFs), grupos parentais desconhecidos (UPGs) e truncamento de pedigree — metodologias que contribuem para aumentar a acurácia e reduzir o viés na avaliação genômica.
Recomenda-se que o leitor não pule etapas, mesmo que algum conteúdo pareça básico, pois os conceitos iniciais servem de base para as análises mais avançadas.

## Visão geral das metodologias (resumo rápido)

**BLUP (Best Linear Unbiased Prediction — Melhor Predição Linear Não Viesada):** É o método clássico de avaliação genética, que utiliza informações de pedigree e fenótipos para predizer o valor genético dos animais.

**ssGBLUP (Single-step Genomic BLUP — BLUP Genômico em Etapa Única):** É uma extensão do BLUP que integra informações de pedigree, fenótipos e marcadores genômicos em uma única análise. Dessa forma, permite aumentar a acurácia da predição genética, especialmente para animais jovens sem registros fenotípicos.

**UPGs (Unknown Parent Groups ou Grupos Parentais Desconhecidos):** Agrupa indivíduos com pais desconhecidos em classes que tentam capturar diferenças de base genética entre *cohorts*  (um grupo de indivíduos que compartilham uma característica em comum e são acompanhados/observados durante um período de tempo). Ajuda a corrigir vieses quando há falta de pedigree.

**Metafundadores (MFs):** Representam populações fundadoras com uma matriz de relações entre metafundadores que modela níveis de consanguinidade e estrutura entre fundadores. Em SS-GBLUP, MFs permitem alinhar melhor a matriz genômica G com a matriz de pedigree A e corrigir a base genética.

**Truncamento de pedigree:** Remover gerações antigas do pedigree (ou definir pais como desconhecidos a partir de uma data) reduz o custo computacional e, em alguns cenários, melhora a acurácia quando informação antiga é ruidosa ou mal registrada. Porém, pode introduzir viés se feito incorretamente.

## Exemplos em cada seção

Em cada parte deste tutorial serão apresentados exemplos práticos para facilitar a aplicação dos conceitos.
Os arquivos utilizados nos exemplos — como *fenótipo* (`feno.txt`), *pedigree* (`ped.txt`), *arquivos de parâmetros* (`renun.par`) e *genótipos* (`geno.txt`) — são baseados nos dados da aula prática dados para demonstração das metodologias de *Blup, ssGblup, metafundadores (MFs), grupos parentais desconhecidos (UPGs) e truncamento de pedigree*. Link de acesso aos arquivos na pasta ().

O arquivo geno.txt contém as informações de marcadores SNP de cada animal.

Ele é utilizado para:

+ Construir a matriz genômica (G), essencial nas análises ssGBLUP;

+ Permitir a predição de valores genéticos estimados (GEBVs), aumentando a acurácia em relação ao BLUP tradicional;

+ Integrar dados de genótipo e pedigree, possibilitando a modelagem com metafundadores e correção de base genética.

Todos os exemplos estarão *destacados em caixas* ao longo do texto, permitindo que o leitor identifique rapidamente os arquivos, comandos e saídas necessários para reproduzir as análises em seu próprio ambiente de trabalho.

### Exemplo modelo animal

Dados de exemplo:

Tabela 1. Informações fenotípicas, pedigree e grupo contemporâneo utilizadas para ajuste do modelo animal, considerando pesos ajustados aos 205 dias de idade

| Touros | Filhos (identificação) | Rebanho (grupo contemporâneo) | Peso (kg) aos 205 dias|
|:------:|:----------------------:|:-----------------------------:|:-----------------------:|
| 1 | 1(5)  | B | 205 |
| 1 | 2(6)  | B | 198 |
| 1 | 3(7)  | A | 130 |
| 2 | 1(8)  | A | 156 |
| 2 | 2(9)  | A | 200 |
| 3 | 1(10) | B | 195 |
| 3 | 2(11) | B | 165 |
| 4 | 1(12) | A | 185 |
| 4 | 2(13) | B | 195 |
| 4 | 3(14) | A | 145 |

Fonte: Adaptado de Pereira (2008).

> **Observação:** o número antes do parêntese é a ordem do filho dentro do touro;

> o número dentro do parêntese é o **ID real do bezerro** (usado no modelo animal).

## Avaliação do Modelo Animal Tradicional (BLUP) – Execução Completa ***vs*** Reduzida

Como executar primeiro o modelo BLUP com todos os animais (modelo “completo”) e, na sequência, rodar o mesmo modelo mas sem os animais jovens (modelo “reduzido”) para comparar componentes de variância, log-verossimilhança e soluções (EBVs), e interpretar a influência dos animais jovens nos resultados.

Os dados apresentados na (Tabela 1) serão utilizados para a realização das avaliações de exemplos (completo) a seguir.

### Passo 1 - Preparação dos dados

+ Conferir os arquivos:

  + `feno.txt` → deve conter os fenótipos (ex.: ID animal, grupo de contemporâneo, valor observado).

  + `ped.txt` → deve conter pedigree (ID animal, pai, mãe).

  Sugestão: abra os dois arquivos no R para checar se as colunas estão corretas:

```r
#ler arquivos
feno <- read.table("feno.txt", header=TRUE)
ped  <- read.table("ped.txt", header=TRUE)

head(feno)
head(ped)
```

Fenótipo `feno.txt`

```csv
5 2 205
6 2 198
7 1 130
8 1 156
9 1 200
10 2 195
11 1 165
12 2 185
13 2 195
14 1 145
```

Pedigree `ped.txt`

```csv
1 0 0
2 0 0
3 0 0
4 0 0
5 1 0
6 1 0
7 1 0
8 2 0
9 2 0
10 3 0
11 3 0
12 4 0
13 4 0
14 4 0
```

### Passo 2 - Padronizar IDs

+ Estrutura geral de um .par para BLUPF90+

  + Os IDs precisam ser numéricos consecutivos (1, 2, 3, …).

  + O software `BLUPF90+` exige isso → usamos o `renumf90` para gerar IDs renumerados.

### Coração da análise

**Criar o arquivo de parâmetros** (.par) dizendo ao BLUPF90+ quais colunas são ID, fenótipo, grupos fixos etc.

+ Exemplo (`feno.txt` tenha 3 colunas: **ID animal, grupo contemporâneo, fenótipo**).
  
Cartão de parâmetros `renum.par`

```text
DATAFILE # Nome do arquivo de dados
feno.txt # Fenótipo
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S) # Não há peso, mas deve haver uma linha em branco.

RESIDUAL_VARIANCE # variância residual
628.7
EFFECT
2 cross alpha # 2ª coluna (no exemplo: grupo contemporâneo)
EFFECT
1 cross alpha  #animal
RANDOM
animal
OPTIONAL

FILE
ped.txt
FILE_POS
1 2 3 0 0
PED_DEPTH
0
(CO)VARIANCES # variância aditiva 
128.8
```

**Explicando:**

> TRAITS 3 → fenótipo (característica) está na 3ª coluna.

> EFFECT 2 cross alpha → grupo contemporâneo está na 2ª coluna, como efeito fixo categórico.

> RANDOM animal ped.txt add_animal → efeito aleatório genético aditivo, com pedigree vindo do ped.txt.

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

  + Com um .par inicial para gerar os arquivos `renf90.dat` e `renadd_ped.txt`.

  + Ele também vai criar um novo `renf90.par` adaptado com nomes corretos e renumerados.

```shell
.\renumf90.exe .\renum.par > saida_renum.txt
```

+ Use esse novo .par final para rodar o BLUPF90+.exe:

Agora você pode executar o BLUPF90+ e obter as soluções.

+ Será feita a estimação dos valores genéticos e/ou parâmetros genéticos.

```shell
.\blupf90+.exe .\renf90.par > saida_blup.txt
```

+ Soluções `solutions`

```Text
trait/effect level  solution
   1   1         1        158.88827938
   1   1         2        196.26296890
   1   2         1         -1.06529608
   1   2         2          0.53837742
   1   2         3         -2.74681293
   1   2         4          0.96631427
   1   2         5          0.00316530
   1   2         6         -0.39392643
   1   2         7          0.98537374
   1   2         8          6.82650990
   1   2         9         -2.39715873
   1   2        10         -4.47279604
   1   2        11         -1.44269439
   1   2        12          3.11713509
   1   2        13          0.39541592
   1   2        14         -2.06984525
```

## Single-step GBLUP

### Passo 1 - Preparação dos dados

Podemos reutilizar os mesmos dados e arquivos de pedigree `ped.txt` e fenótipo `feno.txt`do modelo animal anterior.

Arquivo de genótipo `geno.txt`cada linha ID <espaço> marcador1 marcador2 ... ou ID <espaço> cadeia — confirme o formato exato (colunas separadas por espaço/tabl; ou 1 campo com string).

Exemplo de genótipos `geno.txt`

```text
1  01010011211011011011110012210120000010020100100001001000012211000101202...
2  01121001201010120001210010001011110010011000000101101010001100001001100...
3  10110002110011002000000020110011000000000000010120001000101110000011102...
4  10101001012011020010010112000001120110010000000111102010011110110012211...
5  02010012110000001112001011200020100010010001000000001000021111001110101...
6  01011011200112010010101111110011110010010100001001002010012111110100212...
7  00011112111110011001110011210111000000010100100100001001001211000201101...
8  00021012210011210001101001111112100000021100100102002010001110100012210...
9  02111100200011120002121101111002110020001100000200002010101110001000010...
10 01121012210011001000010110110010010010000100110210100000100110000120202...
11 10200001020012011000010010110011110100000010000011002010010020000002101...
12 10101101122021021021001101010001020010001001000011101000020000100011101...
13 10110001112021020000110102000000110100000100000011002010002110200021111...
14 11211000001010010021120011000001110200010000000001101000021100100112121...
```

### Passo 2 - Padronizar IDs

O arquivo de parâmetros `renum2.par`, com opção para ler um arquivo de marcador `geno.txt`.

Cartão de parâmetros `renum2.par`

```text
DATAFILE
feno.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S)

RESIDUAL_VARIANCE  # variances are from aireml results
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
animal
OPTIONAL

FILE
ped.txt
SNP_FILE
geno.txt
PED_DEPTH
0
(CO)VARIANCES
128.8
OPTION solution mean
OPTION EM-REML 25
OPTION conv crit 1e-15
```

As OPTIONS não mudam a estrutura do modelo, apenas dizem como o programa deve rodar (centralizar soluções, usar EM ou Algoritmo de Expectação–Maximização, critério de convergência).

Consulta as OPTIONS: (<https://nce.ads.uga.edu/wiki/doku.php?id=readme.blupf90plus>)

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

```shell
.\renumf90.exe .\renum2.par > saida_renum.txt
```

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
.\blupf90+.exe .\renf90.par > saida_Gblup.txt
```

+ Soluções `solutions`

```text
trait/effect level  solution
   1   1         1        158.77967007
   1   1         2        196.11526586
   1   2         1         -0.93501125
   1   2         2          0.62490688
   1   2         3         -2.53692274
   1   2         4          0.87139135
   1   2         5          0.10416228
   1   2         6         -0.14444765
   1   2         7          1.06316855
   1   2         8          6.93494732
   1   2         9         -2.22593319
   1   2        10         -4.23094078
   1   2        11         -1.26791610
   1   2        12          3.18544363
   1   2        13          0.61155085
   1   2        14         -2.14292571
```

## Grupos Parentais Desconhecidos (UPGs) - BLUP

Nesta etapa, incluímos no modelo a correção para pais desconhecidos através dos UPG (Unknown Parent Groups).

O objetivo é ajustar os valores genéticos dos animais quando há indivíduos sem pai ou mãe conhecidos, evitando viés nas estimativas.

Tabela 2. Número de pais desconhecidos incluídos em cada UPG

|  Grupo UPG  | Tipo de parente             | Nº de animais | Nº de animais genotipados |
| :---------: | :-------------------------: | :-----------: | :------------------------:|
| 1 (−1)| Pais desconhecidos – Grupo 1 | 2 | 2 |
| 2 (−2)| Pais desconhecidos – Grupo 2 | 2 | 2 |
| 3 (−3)| Mães desconhecidas – Grupo 1 | 7 | 7 |
| 4 (−4)| Mães desconhecidas – Grupo 2 | 7 | 7 |
| **Total** |                              | **18**| **18**|

> **Observação**: o número de animais do rebanho real não mudou (segue sendo 14).
> O que acontece é que o programa expande o pedigree para incluir os 4 grupos fictícios (UPGs), resultando em 18 linhas.

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno.txt`e Pedigree com UPG: `ped._upg4.txt`.

+ Fenótipo: `feno.txt`

+ Pedigree com UPG: `ped._upg4.txt`

Aqui, todos os `0` indicam pais desconhecidos. Para usar UPGs com o `RENUMF90`, precisamos substituir esses **zeros** por números **negativos** que representam grupos de origem diferentes (por exemplo, ano ou geração).

Pedigree inicial exemplo:`ped.txt`

```csv
animal  pai  mãe
1       0    0
2       0    0
3       0    0
4       0    0
5       1    0
6       1    0
7       1    0
8       2    0
9       2    0
10      3    0
11      3    0
12      4    0
13      4    0
14      4    0
```

Pedigree editado UPG `ped_upg4.txt`

```csv
1  -1 -3
2  -2 -4
3  -1 -3
4  -2 -4
5   1 -3
6   1 -4
7   1 -3
8   2 -4
9   2 -3
10  3 -4
11  3 -3
12  4 -4
13  4 -3
14  4 -4
```

>UPGs de pais desconhecidos: −1 e −2

>UPGs de mães desconhecidas: −3 e −4

### Passo 2 - Padronizar IDs

+ Estrutura geral de um .par para BLUPF90+

  + Os IDs precisam ser numéricos consecutivos (1, 2, 3, …).

  + O software BLUPF90+ exige isso → usamos o renumf90 para gerar IDs renumerados.

### Coração da análise

**Criar o arquivo de parâmetros** (.par) dizendo ao BLUPF90+ quais colunas são ID, fenótipo, grupos fixos etc.

+ Exemplo (feno.txt tenha 3 colunas: **ID animal, grupo contemporâneo, fenótipo**).
  
Cartão de parâmetros `renun3.par`

```text
DATAFILE
feno.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S)

RESIDUAL_VARIANCE  # variances are from aireml results
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
diagonal
(CO)VARIANCES
128.8
EFFECT
1 cross alpha  #animal
RANDOM
animal
FILE
ped_upg4.txt
#SNP_FILE
#geno.txt
PED_DEPTH
0
UPG_TYPE
in_pedigrees
INBREEDING
pedigree
(CO)VARIANCES
400.0

OPTION solution mean
OPTION random_upg 1
OPTION EM-REML 25
OPTION conv crit 1e-15
```

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

```shell
.\renumf90.exe .\renum3.par > saida_renum.txt
```

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
.\blupf90+.exe .\renf90.par > saida_blup.txt
```

+ Soluções `solutions`

```text
trait/effect level  solution
   1   1         1        158.37167138
   1   1         2        197.12426992
   1   2         1         -0.17817264
   1   2         2          0.57443958
   1   2         3         -1.05352045
   1   2         4         -0.14899075
   1   2         5         -1.20543793
   1   2         6          0.95984737
   1   2         7          0.42067917
   1   2         8         -3.45462093
   1   2         9         -0.47974957
   1   2        10          4.56554378
   1   3         1         -1.24784566
   1   3         2          2.23054361
   1   3         3         -6.28230123
   1   3         4          0.45004223
   1   3         5         -1.07652070
   1   3         6         -1.59875438
   1   3         7          3.25003742
   1   3         8         14.77758286
   1   3         9         -5.92835251
   1   3        10         -8.05417518
   1   3        11         -2.58485229
   1   3        12          5.70880868
   1   3        13          1.25049307
   1   3        14         -4.37452319
   1   3        15         -1.30247340
   1   3        16          1.30242991
   1   3        17          2.57328026
   1   3        18         -2.57327786
   ```

## Grupos Parentais Desconhecidos (UPGs) - ssGBLUP

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno.txt`, Pedigree com UPG: `ped._upg4.txt`, Genótipo`geno.txt`.

+ Fenótipo: `feno.txt`

+ Pedigree com UPG: `ped._upg4.txt`

+ Genótipo`geno.txt`

### Passo 2 - Padronizar IDs

O BLUPF90+ exige IDs contínuos; por isso usamos o `renumf90` para renumerar animais e gerar o arquivo `renf90.par`.

Cartão de parâmetros `renum4.par`

```text
DATAFILE
feno.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S)

RESIDUAL_VARIANCE  # variances are from aireml results
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
diagonal
(CO)VARIANCES
128.8
EFFECT
1 cross alpha  #animal
RANDOM
animal
FILE
ped_upg4.txt
SNP_FILE
geno.txt
PED_DEPTH
0
UPG_TYPE
in_pedigrees
INBREEDING
pedigree
(CO)VARIANCES
400.0

OPTION solution mean
OPTION random_upg 1
OPTION EM-REML 25
OPTION conv crit 1e-15
```

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

```shell
.\renumf90.exe .\renum4.par > saida_renum.txt
```

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
.\blupf90+.exe .\renf90.par > saida_Gblup.txt
```

+ Soluções `solutions`

```text
trait/effect level  solution
   1   1         1        156.91953685
   1   1         2        195.68275414
   1   2         1         -0.18179508
   1   2         2          0.55233423
   1   2         3         -1.06170509
   1   2         4         -0.14033059
   1   2         5         -1.21754529
   1   2         6          0.99225371
   1   2         7          0.39159506
   1   2         8         -3.48930403
   1   2         9         -0.39615177
   1   2        10          4.55065243
   1   3         1          0.14247276
   1   3         2          3.48157231
   1   3         3         -4.75901359
   1   3         4          1.41034335
   1   3         5          0.38644902
   1   3         6          0.01430263
   1   3         7          4.83221235
   1   3         8         16.31702740
   1   3         9         -4.43855112
   1   3        10         -6.39828197
   1   3        11         -1.60045318
   1   3        12          6.58264238
   1   3        13          2.79457783
   1   3        14         -4.11337888
   1   3        15         -0.93075984
   1   3        16          1.26207808
   1   3        17          3.98637864
   1   3        18         -1.31687192
```

## Truncamento de Pedigree - BLUP

O truncamento do pedigree é controlado pelo comando **PED_DEPTH**, que deve ser incluído diretamente no **cartão de parâmetros** usado no renumf90/blupf90. Esse comando informa ao programa **quantas gerações de ancestrais** serão mantidas para cada animal com fenótipo: por exemplo, `PED_DEPTH 1` considera apenas os pais, `PED_DEPTH 2` inclui pais e avós, e assim por diante. Dessa forma, o usuário pode ajustar no arquivo de parâmetros o nível de truncamento desejado conforme os objetivos da análise.

No pedigree original `ped.txt`, os dados possuíam apenas **fundadores e seus filhos**, o que impossibilitava observar diferenças entre os níveis de truncamento. Por isso, utilizei um **pedigree simulado** com mais gerações, permitindo demonstrar de forma prática como o truncamento atua: ao variar o valor de `PED_DEPTH`, o programa reduz progressivamente a profundidade do pedigree considerado na avaliação genética.

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno_expandido.txt`, Pedigree `ped_estendido.txt`.

+ Fenótipo: `feno_expandido.txt`

```text
1 1 195.8
2 1 182.5
3 1 177.4
4 1 150.1
5 2 205.0
6 2 198.0
7 1 130.0
8 1 156.0
9 1 200.0
10 2 195.0
11 1 165.0
12 2 185.0
13 2 195.0
14 1 145.0
15 2 188.7
16 1 181.8
17 1 150.6
18 2 168.1
19 1 164.7
20 1 185.1
21 1 174.2
22 1 162.7
23 1 197.5
24 1 175.2
25 2 211.8
26 2 202.1
27 1 176.9
28 2 155.4
29 1 144.4
30 2 167.9
31 1 178.3
32 1 174.1
33 2 219.2
34 1 176.4
35 2 175.0
36 2 208.0
37 1 170.6
38 2 190.0
39 1 170.5
40 1 172.2
```

+ Pedigree: `ped_estendido.txt`

```text
# ped_estendido.txt — pedigree ampliado (animais 1..40)
1 0 0
2 0 0
3 0 0
4 0 0
5 1 0
6 1 0
7 1 0
8 2 0
9 2 0
10 3 0
11 3 0
12 4 0
13 4 0
14 4 0
15 5 10
16 6 11
17 7 12
18 8 13
19 9 14
20 5 11
21 6 12
22 7 13
23 8 14
24 9 10
25 15 20
26 16 21
27 17 22
28 18 23
29 19 24
30 15 21
31 16 22
32 17 23
33 18 24
34 19 20
35 25 30
36 26 31
37 27 32
38 28 33
39 29 34
40 25 31
```

**Observações**

> Fundadores: 1,2,3,4 (pai=0 e mãe=0).

> Geração 1: 5–14 (filhos dos fundadores).

> Geração 2: 15–24 (filhos de 5–14).

> Geração 3: 25–34 (netos dos fundadores).

> Geração 4: 35–40 (bisnetos dos fundadores).

### Passo 2 - Padronizar IDs

O BLUPF90+ exige IDs contínuos; por isso usamos o `renumf90` para renumerar animais e gerar o arquivo `renf90.par`.

Cartão de parâmetros `renum5.par`

```text
DATAFILE
feno_expandido.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S)

RESIDUAL_VARIANCE  # variances are from aireml results
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
diagonal
(CO)VARIANCES
128.8
EFFECT
1 cross alpha  #animal
RANDOM
animal
FILE
ped_estendido.txt
#SNP_FILE
#geno.txt
PED_DEPTH
3

#OPTION method VCE
OPTION solution mean
OPTION EM-REML 25
OPTION conv crit 1e-15
OPTION alpha_size 40
OPTION max_field_readine 50
```

**Se você colocar:**

> PED_DEPTH 2 → mantém pais e avós.

> PED_DEPTH 3 → mantém pais, avós e bisavós…

> PED_DEPTH 0 → mantém todo o pedigree original, sem truncamento.

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

```shell
.\renumf90.exe .\renum5.par > saida_renum.txt
```

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
.\blupf90+.exe .\renf90.par > saida_blup.txt
```

+ Soluções `solutions`

```text
trait/effect level  solution
   1   1         1        170.28148126
   1   1         2        190.94471270
   1   2         1          4.33360507
   1   2         2          0.68714727
   1   2         3         -0.90386083
   1   2         4         -1.00349913
   1   2         5          0.69568149
   1   2         6         -4.28913144
   1   2         7         -0.38476059
   1   2         8          1.94912042
   1   2         9         -3.33880528
   1   2        10         -3.87717254
   1   2        11         -0.94540560
   1   2        12          2.07448937
   1   2        13          2.51083256
   1   2        14          0.66700203
   1   2        15         -1.28409112
   1   2        16          4.63265009
   1   2        17          0.83159128
   1   2        18          3.53859298
   1   2        19          1.89021821
   1   2        20          1.13095283
   1   2        21         -6.03385086
   1   2        22         -4.39836076
   1   2        23          1.20614072
   1   2        24         -3.91606547
   1   2        25          1.35925736
   1   2        26          0.65497261
   1   2        27          4.80244085
   1   2        28          1.03706579
   1   2        29         -2.71210406
   1   2        30          2.89284524
   1   2        31          0.05976659
   1   2        32         -0.15652174
   1   2        33          0.03666394
   1   2        34         -3.42158721
   1   2        35          0.32019689
   1   2        36          2.38363661
   1   2        37          1.19337668
   1   2        38         -6.84428410
   1   2        39         -2.42613729
   1   2        40          5.04739510
   1   3         1         -0.05838064
   1   3         2         -0.04524471
   1   3         3         -0.02419588
   1   3         4          0.03373777
   1   3         5          0.04405817
   1   3         6         -0.04294463
   1   3         7          0.01109597
   1   3         8          0.05180389
   1   3         9          0.01802116
   1   3        10         -0.04225676
   1   3        11         -0.02878871
   1   3        12          0.00290179
   1   3        13          0.03850131
   1   3        14         -0.03618194
   1   3        15          0.01932689
   1   3        16         -0.00425249
   1   3        17          0.03659816
   1   3        18         -0.02134412
   1   3        19         -0.03284637
   1   3        20         -0.05617922
   1   3        21          0.00572297
   1   3        22         -0.02946106
   1   3        23         -0.01353028
   1   3        24          0.02495193
   1   3        25         -0.05838644
   1   3        26         -0.01284277
   1   3        27          0.01812474
   1   3        28          0.04183415
   1   3        29         -0.02706179
   1   3        30          0.01401234
   1   3        31          0.03168350
   1   3        32          0.02445609
   1   3        33          0.03677137
   1   3        34         -0.01379058
   1   3        35          0.05534756
   1   3        36         -0.03296040
   1   3        37          0.02777029
   1   3        38          0.03432507
   1   3        39         -0.03349473
   1   3        40          0.03538345
```

## Truncamento de Pedigree - ssGBLUP

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno_expandido.txt`, Pedigree `ped_estendido.txt`, Genótipo`geno_40.txt`.

+ Fenótipo: `feno_expandido.txt`

+ Pedigree: `ped_estendido.txt`

+ Genótipo`geno_40.txt`

```text
1  010100112110110110111100122101200000100201001000010010000122110001...
2  011210012010101200012100100010111100100110000001011010100011000010...
3  101100021100110020000000201100110000000000000101200010001011100000...
4  101010010120110200100101120000011201100100000001111020100111101100...
5  020100121100000011120010112000201000100100010000000010000211110011...
6  010110112001120100101011111100111100100101000010010020100121111101...
7  000111121111100110011100112101110000000101001001000010010012110002...
8  000210122100112100011010011111121000000211001001020020100011101000...
9  021111002000111200021211011110021100200011000002000020101011100010...
10 011210122100110010000101101100100100100001001102101000001001100001...
11 102000010200120110000100101100111101000000100000110020100100200000...
12 101011011220210210210011010100010200100010010000111010000200001000...
13 101100011120210200001101020000001101000001000000110020100021102000...
14 112110000010100100211200110000011102000100000000011010000211001001...
15 021210122200000010110110011100100000100001010101000010001101110001...
16 111100111100020100000111011200121200100100000000010020000210210100...
17 000020111221210210111111101001020100000010010000000010010111101001...
18 100210112010201200010110020010110000000112000000020020100010202000...
19 022010001000101200111210110010022101100101000001010010101101101010...
20 011100121200010011010010112100211101100100010000100020100101210000...
21 010121012110210200201012020100120100100100000000000020000110102000...
22 100201011211100210011001021000110101000102001000100020000022211001...
23 111210111010011100100110120100111101000110000001010020000122001001...
24 011111012100211110010110002000111100100001001002001010000000100000...
25 022210221200010000010120101000110000100000000101100010001200200001...
26 011010002110120200101012011100221100000200000000000020000200101000...
27 100110100220100210112010011001020101000011001000100020010022102000...
28 211200111010100100110100120000121001000211000000020020000111101001...
29 012110001100101110011100011010021100100002000002010000001100201000...
30 010110022100110100101011021100110100100101010001000010000101201000...
31 001100102210110210010001010100120201000101001000000020000111220100...
32 101110211110101200111020111000111101000110010000000020000122001001...
33 010120012000212110010000011000210100000102000001011010100010201000...
34 022100111100001101011110001010111002000100000000110010100101201000...
35 011100122100110100110011110000000000200100000000100010000201201001...
36 011100002100110210010011011100221100000101000000000020000100211100...
37 001020200220101210121020121000111101000020010000000020000022002000...
38 120210111000201110000000011000121001000101000000020010000000101001...
39 012110111200102110001100011010010001100101000001000010000101202000...
40 012210111200110110020110111100110100000000001000000010001200210100...
```

### Passo 2 - Padronizar IDs

O BLUPF90+ exige IDs contínuos; por isso usamos o `renumf90` para renumerar animais e gerar o arquivo `renf90.par`.

Cartão de parâmetros `renum6.par`

```text
DATAFILE
feno_expandido.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT(S)

RESIDUAL_VARIANCE  # variances are from aireml results
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
diagonal
(CO)VARIANCES
128.8
EFFECT
1 cross alpha  #animal
RANDOM
animal
FILE
ped_estendido.txt
SNP_FILE
geno_40.txt
PED_DEPTH
3

#OPTION method VCE
OPTION solution mean
OPTION EM-REML 25
OPTION conv crit 1e-15
OPTION alpha_size 40
OPTION max_field_readine 50
```

### Passo 3 - Rodar no Prompt de Comando do Windows

+ Rode `renumf90.exe`:

```shell
.\renumf90.exe .\renum6.par > saida_renum.txt
```

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
.\blupf90+.exe .\renf90.par > saida_gblup.txt
```

+ Soluções `solutions`

```text
trait/effect level  solution
   1   1         1        170.28144666
   1   1         2        190.94428218
   1   2         1          4.33368035
   1   2         2          0.68726744
   1   2         3         -0.90368362
   1   2         4         -1.00414883
   1   2         5          0.69592230
   1   2         6         -4.28960536
   1   2         7         -0.38498881
   1   2         8          1.94946081
   1   2         9         -3.33847710
   1   2        10         -3.87678130
   1   2        11         -0.94537541
   1   2        12          2.07454660
   1   2        13          2.51087849
   1   2        14          0.66674558
   1   2        15         -1.28443522
   1   2        16          4.63276978
   1   2        17          0.83146576
   1   2        18          3.53880137
   1   2        19          1.89029088
   1   2        20          1.13157101
   1   2        21         -6.03356157
   1   2        22         -4.39872436
   1   2        23          1.20597779
   1   2        24         -3.91673548
   1   2        25          1.35946119
   1   2        26          0.65448819
   1   2        27          4.80286266
   1   2        28          1.03753848
   1   2        29         -2.71247749
   1   2        30          2.89277556
   1   2        31          0.05975358
   1   2        32         -0.15621699
   1   2        33          0.03670064
   1   2        34         -3.42168782
   1   2        35          0.32034163
   1   2        36          2.38358024
   1   2        37          1.19341238
   1   2        38         -6.84475369
   1   2        39         -2.42578906
   1   2        40          5.04714867
   1   3         1         -0.05776725
   1   3         2         -0.04715601
   1   3         3         -0.02553559
   1   3         4          0.03520562
   1   3         5          0.04328412
   1   3         6         -0.03867073
   1   3         7          0.00906679
   1   3         8          0.05155493
   1   3         9          0.01770730
   1   3        10         -0.04410603
   1   3        11         -0.02600792
   1   3        12          0.00270099
   1   3        13          0.03852517
   1   3        14         -0.03714989
   1   3        15          0.01656999
   1   3        16         -0.00272371
   1   3        17          0.03738373
   1   3        18         -0.02149939
   1   3        19         -0.03646228
   1   3        20         -0.05337196
   1   3        21          0.00836920
   1   3        22         -0.02741845
   1   3        23         -0.00914086
   1   3        24          0.02593318
   1   3        25         -0.05963571
   1   3        26         -0.01486797
   1   3        27          0.01991680
   1   3        28          0.04269781
   1   3        29         -0.02775011
   1   3        30          0.01375878
   1   3        31          0.03125935
   1   3        32          0.02327841
   1   3        33          0.03701389
   1   3        34         -0.01163305
   1   3        35          0.05336535
   1   3        36         -0.03285886
   1   3        37          0.02853064
   1   3        38          0.03330220
   1   3        39         -0.03062555
   1   3        40          0.03455360
```

# Procedimento para Execução do Programa `gammaf90` e Solução de Erros de Biblioteca

## Objetivo

Orientar o usuário quanto à instalação e configuração corretas das bibliotecas necessárias para executar os programas da família `BLUPF90+`, em especial o `gammaf90`, garantindo o funcionamento adequado no ambiente **Linux** (WSL/Ubuntu).

## Descrição

Durante a execução do programa `gammaf90` (ou de outros executáveis da família `BLUPF90+`), pode ocorrer o seguinte erro no terminal:

```shell
./gammaf90.date: error while loading shared libraries: libmkl_intel_lp64.so.2: cannot open shared object file: No such file or directory
```

Esse erro indica que o sistema não encontrou as bibliotecas matemáticas da **Intel® oneAPI Math Kernel Library (oneMKL)**, necessárias para a execução dos programas.
Para corrigir, deve-se instalar a biblioteca e configurar o ambiente conforme descrito abaixo.

## Procedimento passo a passo

### Instalação das bibliotecas Intel oneMKL

1. Atualizar o sistema e instalar pré-requisitos:

```shell
sudo apt update
sudo apt install -y gpg-agent wget
```

2. Adicionar a chave de autenticação Intel ao sistema:

```shell
wget -O- https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS.PUB \
| gpg --dearmor | sudo tee /usr/share/keyrings/oneapi-archive-keyring.gpg > /dev/null
```

3. Adicionar o repositório Intel ao gerenciador APT:

```shell
echo "deb [signed-by=/usr/share/keyrings/oneapi-archive-keyring.gpg] https://apt.repos.intel.com/oneapi all main" \
| sudo tee /etc/apt/sources.list.d/oneAPI.list
```

4. Atualizar a lista de pacotes:

```shell
sudo apt update
```

5. Instalar a biblioteca Intel® oneAPI Math Kernel Library (oneMKL):

```shell
sudo apt install intel-oneapi-mkl
```

6. Uma vez instalada a biblioteca, você precisa adicioná-la à variável de ambiente `LD_LIBRARY_PATH` para que o sistema possa encontrá-la durante a execução das aplicações. A melhor forma de fazer isso é executar o script de configuração do ambiente Intel que define todos os caminhos automaticamente.

**Para configuração temporária (válida apenas até fechar o terminal):**

```shell
source /opt/intel/oneapi/setvars.sh
```

**Para configuração permanente (executada automaticamente a cada inicialização):**

```shell
echo 'source /opt/intel/oneapi/setvars.sh' >> ~/.bashrc
source ~/.bashrc
```

7. Verificação da instalação.

**Após seguir os passos anteriores, verifique se o `gammaf90` está funcionando corretamente executando:**

```shell
./gammaf90 < gamma.par
```

Se o programa iniciar sem apresentar erros de biblioteca, a configuração foi concluída com sucesso.

## Metafundadores - (Procedimento completo para uso do gammaf90 e análise com metafundadores)

### Objetivo

Estabelecer o fluxo operacional para geração e uso de metafundadores nas análises genéticas com os programas da família BLUPF90, utilizando o `gammaf90` para criação da matriz Γ (Gamma) e o `blupf90+` para execução da análise.

### Descrição

Os metafundadores são pseudoindivíduos teóricos que representam a origem genética comum dos animais da base do pedigree (fundadores), permitindo modelar o relacionamento entre populações ancestrais.
A inclusão de metafundadores melhora a precisão das análises genéticas ao ajustar a matriz de parentesco (A) para uma versão expandida (A(Γ)), que considera o relacionamento entre fundadores.

O programa `gammaf90` é responsável por gerar a matriz Γ e um novo pedigree com metafundadores, enquanto o blupf90+ realiza a análise genética utilizando essas informações.

O programa `gammaf90` faz parte da família de programas BLUPF90 e deve ser solicitado diretamente ao grupo desenvolvedor da Universidade da Geórgia (EUA), por meio do e-mail *<blupf90@uga.edu>*, mediante autorização para uso acadêmico. `https://nce.ads.uga.edu/software/`

As análises genéticas podem ser conduzidas de duas formas:

> Avaliação tradicional (BLUP Animal): utilizando apenas pedigree e fenótipos.

> Avaliação genômica (ssGBLUP): integrando informações fenotípicas, genealógicas e genotípicas (SNPs).

Ambas as metodologias podem incorporar metafundadores (`gammaf90`) para correção das relações genéticas entre animais fundadores.

### Passo 1 - Preparação dos dados

Criação de Metafundadores (MFs) no Pedigree.

Você deve definir quantos metafundadores (MFs) quer ter.

Eles representam grupos genéticos antigos — por exemplo, diferentes bases ou raças fundadoras.

Exemplo:

MF1 = base Angus

MF2 = base Brangus

MF3 = base Nelore

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno_expandido.txt`e Pedigree `ped_estendido.txt`.

+ Fenótipo: `feno_expandido.txt`

+ Pedigree: `ped_estendido.txt`

Objetivo

Gerar um novo arquivo de pedigree (ped_meta.txt) onde os pais desconhecidos (0) são substituídos por metafundadores (-MF1, -MF2, ...), para uso em análises genéticas com o pacote BLUPF90+.

**Configurar ambiente no RStudio**

Antes de tudo, aponte o diretório onde estão seus arquivos:

```shell
# Definir diretório de trabalho
setwd("C:/Users/SeuUsuario/Downloads")  # ajuste o caminho conforme sua pasta

# Verificar se os arquivos estão lá
list.files()
```

Você deve ver algo como:

```shell
[1] "ped_estendido.txt" "renum7_meta.par"
```

Carregar o pedigree original

```shell
# Carregar pacotes necessários
library(tidyverse)

# Ler o arquivo de pedigree
ped <- read.table("ped_estendido.txt", header = FALSE)
colnames(ped) <- c("animal", "pai", "mae")

# Visualizar as primeiras linhas
head(ped)
```

Definir os Metafundadores

Defina quantos MFs você deseja criar e como eles serão atribuídos.

```shell
# Definir nomes dos metafundadores
MFs <- c("MF1", "MF2", "MF3")  # você pode mudar o número ou os nomes
```

Substituir os pais desconhecidos (0) pelos MFs

Aqui você tem duas opções:

🔸 Opção A — Aleatória (cada linha recebe um MF sorteado)

Ideal para dados sem estrutura prévia de grupos fundadores.

```shell
set.seed(123)  # garante reprodutibilidade

ped <- ped %>%
  mutate(
    pai = ifelse(pai == 0, paste0("-", sample(MFs, n(), replace = TRUE)), pai),
    mae = ifelse(mae == 0, paste0("-", sample(MFs, n(), replace = TRUE)), mae)
  )
```

🔸 Opção B — Por intervalo de IDs

Útil se você quer que animais de certas faixas usem um MF específico.

```shell
ped <- ped %>%
  mutate(
    pai = case_when(
      pai == 0 & animal <= 10 ~ "-MF1",
      pai == 0 & animal <= 20 ~ "-MF2",
      pai == 0 ~ "-MF3",
      TRUE ~ as.character(pai)
    ),
    mae = case_when(
      mae == 0 & animal <= 10 ~ "-MF1",
      mae == 0 & animal <= 20 ~ "-MF2",
      mae == 0 ~ "-MF3",
      TRUE ~ as.character(mae)
    )
  )
```

Salvar o novo pedigree

```shell
write.table(ped, "ped_meta.txt", row.names = FALSE, col.names = FALSE, quote = FALSE)
cat("✅ Arquivo 'ped_meta.txt' criado com sucesso!\n")
```

onferir resultado

Abra o arquivo `ped_meta.txt` e verifique se os pais desconhecidos foram substituídos corretamente:

```shell
1 -MF1 -MF3
2 -MF2 -MF1
3 -MF3 -MF2
4 -MF1 -MF2
5 1 -MF1
6 1 -MF3
```

### Passo 2 - Padronizar IDs

O BLUPF90+ exige IDs contínuos; por isso usamos o `renumf90` para renumerar animais e gerar o arquivo `renf90.par`.

Cartão de parâmetros `renum7_meta.par`

```text
DATAFILE
feno_expandido.txt
TRAITS
3
FIELDS_PASSED TO OUTPUT
1
WEIGHT

RESIDUAL_VARIANCE
628.7
EFFECT
2 cross alpha
EFFECT
1 cross alpha  #animal
RANDOM
diagonal
(CO)VARIANCES
128.8
EFFECT
1 cross alpha  #animal
RANDOM
animal
FILE
ped_meta.txt
SNP_FILE
#geno_40.txt
PED_DEPTH
0
UPG_TYPE
in_pedigrees

#OPTION method VCE
#OPTION solution mean
#OPTION EM-REML 25
#OPTION conv crit 1e-15
#OPTION alpha_size 40
#OPTION max_field_readine 50
#OPTION metafounders gamma
```

### Passo 3 - Rodar no Prompt de Comando do Linux

+ Rode `renumf90`:

```shell
./renumf90 ./renum7_meta.par > saida_renum.txt
```

Verificar se foram gerados os seguintes arquivos:

> `renf90.par` → parâmetros prontos para análise;

> `renadd03.ped` → pedigree renumerado;

> `renf90.dat` → dados fenotípicos renumerados.

### Passo 4 - Geração da matriz de metafundadores (Γ)

1. Executar o comando:

```shell
./gammaf90.date --snpfile geno_40.txt --pedfile renadd03.ped > saida_gammaf90.txt
```

Arquivos gerados:

> Valor médio de Γ apresentado no txt (`saida_gammaf90.txt`).

Verificar se foram gerados os seguintes arquivos:

> gamma.txt

Renomeie o arquivo de saída "`gamma.txt`" para "`renadd03.ped_gamma`".

Substitua "add_an_animal" (ou "add_an_upg" ou "add_an_upginb") no renf90.par por "`add_an_meta`".

+ Agora você pode executar o BLUPF90+ e obter as soluções.

```shell
./blupf90+.exe ./renf90.par > saida_gblup.txt
```

Relatório de execução da análise com metafundadores.

+ Soluções `solutions`

Soluções dos efeitos fixos e valores genéticos preditos.

```text

```

## Referência

Aguilar, I., S. Tsuruta, Y. Masuda, D. A. L. Lourenco, A. Legarra, I. Misztal. 2018. BLUPF90 suite of programs for animal breeding with focus on genomics. No. 11.751. The 11th World Congress of Genetics Applied to Livestock Production, Auckland, New Zealand.

Intel Corporation. Get Intel® oneAPI Math Kernel Library (oneMKL).
Disponível em: <https://www.intel.com/content/www/us/en/developer/tools/oneapi/onemkl-download.html>

Lourenco, D. A. L., Legarra, A., Tsuruta, S., Masuda, Y., Aguilar, A., Misztal, I. 2020. SingleStep Genomic Evaluations from Theory to Practice: Using SNP Chips and Sequence Data in BLUPF90. Genes, 11:790. <https://doi.org/10.3390/genes11070790>

Lourenco, D. A. L., Tsuruta, S., Masuda, Y., Bermann, M., Legarra, A., Misztal, I. Recent updates in the BLUPF90 software suite. In: Proceedings of the 12th World Congress on Genetics Applied to Livestock Production; 2022 July 3-8; Rotterdam.

Masuda, Y. 2018. Introduction to BLUPF90 suite programs. University of Georgia. <http://nce.ads.uga.edu/wiki/doku.php?id=documentation>

Misztal, I., S. Tsuruta, D. A. L. Lourenco, Y. Masuda, I. Aguilar, A. Legarra, Z. Vitezica. 2014.
Manual for BLUPF90 family programs. University of Georgia. <http://nce.ads.uga.edu/wiki/doku.php?id=documentation>

PEREIRA, J. C. C. 2008. Melhoramento genético aplicado à produção animal. 5ª ed. Belo Horizonte: FEPMVZ Editora, 617 p. ISBN 978-85-87144-30-0.
