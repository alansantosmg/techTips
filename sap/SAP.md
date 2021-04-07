# Atalhos SAP

## Atalhos 

| Atalho      | funcao                                              |
| ----------- | --------------------------------------------------- |
| `Shift F6`  | sair do sap                                         |
| `F3`        | voltar                                              |
| `Shift F3`  | sair                                                |
| `/nfd03`    | Sai da transação atual e vai para fd03              |
| `/ofd03`    | Abre nova janela c/ transação fd03                  |
| `/nex`      | Sair de todas as janelas e fechar next, exit sessão |
| `F1`        | ajuda de campos                                     |
| `F4`        | Abre match code. Caixa de pesquisa do campo         |
| `alt` `F12` | Ajustar layout local                                |
| `/i`        | cancela sessão corrente                             |
| `/nend`     | next, end, Fecha janelas e confirma logoff          |
| `/o`        | overview da transação                               |
| `/oXXX`     | Open transação em nova janela                       |
| `F2`        | Executa transação sem enter                         |
| `ctrl` `F`  | busca transações                                    |
| `teste`     | meu teste                                           |





## Tipos de tansações

| número | Tipo       |
| ------ | ---------- |
| 1      | Cadastro   |
| 2      | visualizar |
| 3      | Alterar    |


## SAP Basis

BASIS = Base, Administração, Servidor, Informação, Segurança

Profissional de SAP Basis é responsável pela Infraestrutura do ERP SAP. 


### Basis Best Pratices

#### Como exibir código de transações no menu

Ir em `suplementos`, `configurações` e marcar a opção `exibir nomes técnicos`

#### Como alterar posição dos favoritos.
Ir em `suplementos`, `configurações` e marcar opção de favoritos em cima. 

#### Como Exibir código de campos
Botão na gui: `ajustar layout local` `opções` guia: `especialistas`
Marcar a opção: `Exibir chave em todas listas drop down`

#### Perfil e agenda do d
- `SU3`  Aterar dados do usuário. Definir idioma de logon
- `SSC1` Agenda do usuário

#### Como enviar mensagem rápida para usuário
- `SE37` - Função: `TH_POPUP` + `f8` (testar/executar)
- client: `800`
- user:  `GPUSER1024` (entrar com cód. usuário)

#### Como parametrizar Netweaver ecc
- `SPRO` `IMG Referencia SAP` `SAP Netweaver`
- 

#### Como saber qual a velocidade do sistema
Acessar barra de status no lado inferior direito da GUI.

#### Como acessar intranet do sAP
Clicar no botão bussiness Workplace. Esta é´uma área pessoal com caixa de entrada, saída, e arquivo. 


#### Versões SAP 

##### Versão ECC 6.0
É o antigo R3. Possui finanças e contabilidade. É multi-idioma. Possui 37 idiomas. É multi-empresa, multi-moeda. Suporta operações internacionais. 

##### Versão SRM ou SCM (Logística)
Possível configurar operadores logísticos, porto, ferroviário e aéreo

##### Bussiness One. 
Similar ao ECC, porém tem que sair do ambiente para entrar em outra empresa. Ela náo é multiempresa. 

##### Versão All in one
Versão para médias empresas. É o B1 + Bi + integrações

##### Netweaver
Ambiente web do SAP. 

#### CRM 
Versão intermediária para controlar parte de vendas. Usada para quem trabalha com vendas distribuidas. 

##### SOLMAN (Solution Manager)
Controla as demais soluções/módulos do SAP e suas atualizações de patch e versões, alertas, suporte, service desk e desenvolvimento. Serve para testar mudanças no ambiente. 


##### Bussiness Objects. 
Componente para gerar gráficos, relatórios e é integrada com dispositivos móveis. 

##### HANA
Componente que integra informações. É uma solução bastante robusta com capacidades preditivas. 


### Transações de suporte - bloqueio e desbloqueio de usuários

| Transação | função                           |
| --------- | -------------------------------- |
| SM21      | Verifica logs do sisteam         |
| SM04      | Lista usuarios online (Deslogar) |
| SM01 SM51 | Bloquear transação  SM51         |
| SU01      | Gerenciar usuário                |

Na transação SU01 é possível bloquear ou desbloquear usuário. 
Na transação SM04 se clicar no usuário é possível derrubar o usuário.

Usuário perfil SAP_ALL pode bloquear transações do usuário usando transação SM01 SM51 (final da tela). 
