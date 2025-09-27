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

| Grupo UPG | Tipo de parente              | Nº de animais | Nº de animais genotipados |
| --------- | ---------------------------- | ------------- | ------------------------- |
| 1 (−1)    | Pais desconhecidos – Grupo 1 | 2             | 2                         |
| 2 (−2)    | Pais desconhecidos – Grupo 2 | 2             | 2                         |
| 3 (−3)    | Mães desconhecidas – Grupo 1 | 7             | 7                         |
| 4 (−4)    | Mães desconhecidas – Grupo 2 | 7             | 7                         |
| **Total** |                              | **18**        | **18**                    |

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

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno.txt`, Pedigree com UPG: `ped_upg4.txt`, Genótipo`geno.txt`.

+ Fenótipo: `feno.txt`

+ Pedigree com UPG: `ped.txt`

## Truncamento de Pedigree - ssGBLUP

### Passo 1 - Preparação dos dados

Todos os arquivos necessários para a análise devem estar reunidos na mesma pasta, incluindo o arquivo de fenótipos `feno.txt`, Pedigree com UPG: `ped._upg4.txt`, Genótipo`geno.txt`.

+ Fenótipo: `feno.txt`

+ Pedigree com UPG: `ped.txt`

+ Genótipo`geno.txt`

## Referência

Misztal, I., S. Tsuruta, D. A. L. Lourenco, Y. Masuda, I. Aguilar, A. Legarra, Z. Vitezica. 2014.
Manual for BLUPF90 family programs. University of Georgia. <http://nce.ads.uga.edu/wiki/doku.php?id=documentation>

Masuda, Y. 2018. Introduction to BLUPF90 suite programs. University of Georgia. <http://nce.ads.uga.edu/wiki/doku.php?id=documentation>

Lourenco, D. A. L., Tsuruta, S., Masuda, Y., Bermann, M., Legarra, A., Misztal, I. Recent updates in the BLUPF90 software suite. In: Proceedings of the 12th World Congress on Genetics Applied to Livestock Production; 2022 July 3-8; Rotterdam.

Lourenco, D. A. L., Legarra, A., Tsuruta, S., Masuda, Y., Aguilar, A., Misztal, I. 2020. SingleStep Genomic Evaluations from Theory to Practice: Using SNP Chips and Sequence Data in BLUPF90. Genes, 11:790. <https://doi.org/10.3390/genes11070790>

Aguilar, I., S. Tsuruta, Y. Masuda, D. A. L. Lourenco, A. Legarra, I. Misztal. 2018. BLUPF90 suite of programs for animal breeding with focus on genomics. No. 11.751. The 11th World Congress of Genetics Applied to Livestock Production, Auckland, New Zealand.
