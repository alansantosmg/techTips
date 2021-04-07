Eslint + Prettier Install

## Vim para webdev Parte VI

## Linters

Linter vem da palavra "lint" que significa "fiapo ou penugem". O termo vem de um utilitário usado em programação na Linguagem C no Unix.
O linter fará uma análise estática do código com objetivo de apontar e produzir uma lista de erros, advertências (warnings) e pontos de melhoria. Você não vai querer produzir um tecido cheio de fiapos, não é mesmo?

## Formatadores de código

Os formatadores de código são ferramentas que melhoram a legibilidade de um programa, aplicando regras de formatação em conformidade com as boas práticas de programação para uma determinada linguagem.

Vamos supor por exemplo que temos um código formatado da seguinte maneira:
if (a==b){ printf("x");}

Ao rodar um formatador sobre o código, ele poderá melhorar a legibilidade:

if (a == b) {
printf("x");
}

No caso acima, o utilitário reformatou o código, colocando espaçamento, identação, etc melhorando sua legibilidade e organnização.

## Refatorando

O processo de escrita de código pode ser um tanto maçante e sujeito a erros por parte do programador. Utilitários de verificação de erros e formatadores de código são ferramentas indispensáveis para aumentar a produtividade, pois tornam o código mais legível e poupam tempo do programador na procura de erros simples como um esquecimento de parêntesis ou codificação fora das boas práticas de determinada linguagem, permitindo-o concentrar-se no que é mais importante: a lógica do código.

Quando um desenvolvedor vai utilizar um utilitário de verificação e formatação de código, ele pode fazê-lo de duas formas.
De forma síncrona, neste caso ele digita todo o código e então roda o utilitário de verificação ao salvar o arquivo.
As vantagens dessa estratégia de trabalho são:

- O programador pode se concentrar no código sem se preocupar em parar para ficar consertando errors. É como se ele dividisse seu trabalho em duas etapas: Primeiro codificar, segundo corrigir.
- O programador pode executar a verificação em lote de código, verificando por exemplo vários arquivos de um diretório.
  Desvantagens:
- a desvantagem dessa estratégia é que o utilitário não força a mudança do comportamento do programador. Logo, a evolução do programador para geração de códigos com melhor qualidade acabará sendo mais lenta.
- outra desvantagem é que essa estratégia precisa ocorrer de forma pragmática. Ou seja, o programador precisa ter disciplina suficiente para NUNCA esquecer de executar a etapa de verificação após o término da codificação.

De forma assíncrona: à medida em que vai digitando o utilitário vai verificando o código e alertando sobre os erros.
As vantagens dessa estratégia são:

- Ao terminar de codificar o programador já terá um código com maior qualidade.
- Ao ser alertado por erros enquanto digita, o programador acaba se tornando melhor, pois vai tomando ciência dos erros que produz e ajustando seu comportamento. Digamos que esse método é mais behavorista.
- O programador não precisará executar a verificação em lote ou ao final. Ele pode fazer, mas a lista de erros a corrigir (retrabalho), será bem menor.
  Desvantagens:
- a desvantagem dessa estratégia é que a produtividade do programador acaba sendo mais baixa, pois ele tenderá a parar para corrigir os erros à medida que os mesmos são indicados. Mesmo melhorando com o tempo, isso irá incidir. Só o fato de um alerta aparecer enquanto o código é digitado, pode ser suficiente para desviar parte da concentração do programador.
- outra desvantagem dessa estratégia é que a parametrização dos utilitários para ficarem monitorando o código digitado é um pouco mais chata e além disso, podem tornar o editor de códigos um pouco mais lento. Em alguns momentos o programador pode perceber um "lag" durante a digitação na hora em que o utilitário corre sobre o código e detecta um erro.

## Boas práticas de CI/CD

Bons programadores são antes de tudo, pragmáticos e muitos optam por adotar tanto a estratégia de verificação assíncrona quanto a de verificação síncrona. Ou seja, eles deixam os utilitários de verificação trabalharem enquanto digita o código e irão rodá-los novamente na hora de salvar ou mesmo durante o processo de deploy. Em ambientes de produção aliás, é muito indicado que os processos de CI/CD (integração contínua e deploy contínuo) incluam as etapas de verificação de erros e formatação, impedindo o build e deploy de aplicações com erros de sintaxe ou código mal formatado, aumentando a estabilidade de aplicações em produção.

## Linters e Prettier no Vim.

Existem vários plugins para formatar e verificar erros de código usando o editor Vim. É preciso cuidado ao instalar e utilizar esses plugins, pois os mesmos podem conflitar entre si, podendo acarretar o efeito inverso ao que se propõem. No Vim, muitos programadores desistem de usar tais utilitários justamente pela dificuldade em configurá-los para se obter o resultado esperado. Neste artigo falaremos sobre a instalação não conflitante de 3 plugins:

ALE - Plugin para monitoramento assíncrono de código
ESLint - um utilitário de análise sintática de código
Prettier - um utilitário de formatação de código.

Forma de trabalho: O ALE será utilizado para rodarmos o ESLint enquanto o código é digitado, ajudando a indicar erros de sintaxe no momento e que eles forem aparecendo.

O Prettier será utilizado para formatar o código quando pressionarmos uma tecla específica, permitindo termos mais controle sobre a reformatação, possibilitando inclusive desfazê-la logo após, apenas digitando :u (undo). Fica a critério, incluir uma parametrização para rodá-lo automaticamente ao salvar o arquivo.

# Passo a passo para instalar o ESLINT integrado com o Prettier no VIM

## Instalação dos pacotes requeridos

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install yarn
sudo apt-get install nodejs
sudo apt-get install npm
npm install eslint -g
sudo eslint --init
sudo npm install prettier -g
sudo npm install -g eslint-config-prettier eslint-plugin-prettier
npm install eslint eslint-config-airbnb --global
npm install standard --global (opcional)
npm install eslint-plugin-jsx-a11y@^2.0.0 eslint-plugin-react eslint-plugin-import babel-eslint --global
sudo npm install -g eslint-config-airbnb-base@latest
sudo npm install -g eslint@^4.16.0
sudo npm install -g eslint-plugin-import@^1.18.2
```

Instalação do plugins

Plug 'prettier/vim-prettier', {'do': 'yarn install'}
