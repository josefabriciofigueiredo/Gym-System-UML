# Gym-System-UML
[![NPM](https://img.shields.io/npm/l/react)](https://github.com/josefabriciofigueiredo/Gym-System-UML/blob/main/LICENSE)

## Índice
1. [Levantamento de Requisitos](#levantamento-de-requisitos)
2. [Diagramas](#diagramas)
   - [Diagrama de Caso de Uso](#diagrama-de-caso-de-uso)
      - [Estrutura de Especificação de Casos de Uso](#estrutura-de-especificação-de-casos-de-uso)
   - [Diagrama de Atividades](#diagrama-de-atividades)
   - [Diagrama de Classes](#diagrama-de-classes)
   - [Diagrama de Máquina de Estado](#Diagrama-de-Máquina-de-Estado)

<br>

## Levantamento de Requisitos

### Requisitos Funcionais
| **RF**   | **Descrição**                                                                                                                                                                                                     |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RF001    | O sistema deve cadastrar o aluno, somente presencialmente com o atendente (CPF, Nome, data de nascimento, telefone, e-mail, preferências de treino). Caso tenha mais pessoas da família, opta pelo plano familiar e adicione os seus dependentes. |
| RF002    | O sistema deve liberar o acesso aos recursos da academia para o aluno quando fizer o pagamento da mensalidade.                                                                                                   |
| RF003    | O sistema deve permitir ao aluno que edite seus dados pessoais (Nome, telefone, preferência de treino), como também atualizar seus dados bancários.                                                              |
| RF004    | O sistema deve permitir ao aluno recuperar o acesso da sua conta por meio de e-mail (Envio de um link para alterar a senha).                                                                                     |
| RF005    | O sistema deve possibilitar que somente o professor registre os dados da avaliação técnica dos alunos (Índice de Massa Corporal (IMC), peso, altura, percentual de gordura e quantidade de massa muscular), guardando em um histórico (Sendo realizado a cada 6 meses caso o aluno queira). |
| RF006    | O sistema deve permitir que o aluno agende a avaliação técnica, com disponibilidade baseada nos horários dos professores.                                                                                        |
| RF007    | O sistema deve permitir ao aluno que veja as avaliações técnicas e sua evolução.                                                                                                                                |
| RF008    | O sistema deve permitir todo os alunos que visualize o cronograma da academia (Horários de treinos, eventos e feriados).                                                                                         |
| RF009    | O sistema deve permitir ao professor que registre o treino do aluno, marcando o professor que fez o registro.                                                                                                   |
| RF010    | O sistema deve permitir aos professores que possa editar os treinos colocando vídeos ou guias para os alunos.                                                                                                   |
| RF011    | O sistema deve permitir ao aluno que possa ver seu treino.                                                                                                                                                       |
| RF012    | O sistema deve permitir ao aluno que edite o seu treino ou montar um do zero.                                                                                                                                    |
| RF013    | O sistema deve registrar os históricos dos treinos.                                                                                                                                                              |
| RF014    | O sistema deve enviar uma notificação da mensalidade (Por meio de e-mail com um prazo de uma semana antes, três dias antes e no dia do vencimento), permitindo pagamento por boleto, PIX, cartão de crédito/débito. Caso seja pago em dinheiro, o atendente deve marcar no sistema o pagamento. |
| RF015    | O sistema deve permitir ao aluno que acesse o historio de pagamentos realizados e pendentes (Data, método de pagamento e valor).                                                                                 |
| RF016    | O sistema deve liberar a passagem do aluno da catraca, caso as mensalidades estejam pagas. Se ocorrer alguma falha no sistema, o atendente poderá liberar manualmente.                                           |
| RF017    | O sistema deve permitir ao aluno que veja seus status financeiros.                                                                                                                                               |
| RF018    | O sistema deve bloquear o aluno caso tenha mensalidades pendentes e avisa-lo por meio de e-mail, no app/site permite visualizar a mensalidade pendente.                                                          |
| RF019    | O sistema deve permitir ao administrador que gerencie os funcionários com a criação das contas e se é Professor ou Atendente.                                                                                    |
| RF020    | O sistema deve permitir ao administrador que veja os históricos das frequências dos alunos e popularidade nos treinos.                                                                                           |
| RF021    | O sistema deve permitir ao administrador que atualize as mensalidades e planos da academia e avise os alunos (Por meio de e-mail) com um mês de antecedência a mudança.                                           |
| RF022    | O sistema deve permitir ao administrador que adicione o cronograma da academia, notificando caso ocorra algum evento ou feriado pelo e-mail.                                                                     |

### Requisitos Não Funcionais
| **RNF**   | **Descrição**                                                                                                                                                     |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RNF001    | O sistema deve utilizar o SGBD MySQL para armazenar os dados.                                                                                                     |
| RNF002    | O sistema deve integrar o processamento de pagamentos por meio da API Stripe.                                                                                     |
| RNF003    | O BACKEND do sistema deve ser implementado em Node.JS ou Java com Spring Boot, garantindo escalabilidade e desempenho na camada de serviços.                       |
| RNF004    | O site do sistema deve ser desenvolvido em HTML, CSS e JavaScript.                                                                                                |
| RNF005    | O aplicativo deve ser desenvolvido para plataforma Android utilizando Kotlin como linguagem principal.                                                            |
| RNF006    | O sistema destinado aos atendentes deve ser uma aplicação desktop desenvolvido em Java, garantindo uma interface responsiva.                                      |
| RNF007    | A API deve ser implementada em um servidor executando o SO Linux Debian.                                                                                          |

<br>

## Diagramas

### Diagrama de Caso de Uso
![Diagrama de Caso de Uso](./Diagramas/Diagrama%20de%20Casos%20de%20Uso.jpg)

---

#### Estrutura de Especificação de Casos de Uso
**Identificador:** UC -

**Nome:** Registrar Pagamentos

**Objetivo:** Permitir que o pagamento seja realizado diretamente pelo aluno, ou sendo intermediário pelo atendente, com o sistema processando e atualizando o status.

**Atores:**
- Primário: Atendente, Aluno
- Secundário: Sistema

**Pré-condições:**
- O aluno deve estar cadastrado no sistema
- O aluno deve possuir mensalidades pendentes em aberto

**Cenários:**
- **Fluxo Principal:**
   1.	O aluno acessa no app/site as credenciais validas.
   2.	O aluno abre a aba de mensalidades.
   3.	O aluno seleciona a mensalidade que falta quitar.
   4.	O sistema exibe as informações da forma de pagamento (PIX, BOLETO, CARTÃO DE CRÉDITO/DÉBITO).
   5.	O aluno/atendente confirma o pagamento.
   6.	O sistema registra o pagamento e atualiza o status financeiro.
   7.	O sistema libera o acesso dos recursos da academia.
- **Fluxo Alternativo (1):** Atendente realizando o registro do pagamento.
   - a.	O atendente acessa o sistema desktop com suas credenciais validas.
   - b.	O atendente localiza o aluno pelo CPF ou ID.
   - c.	O atendente seleciona a mensalidade que falta quitar.
   - d.	O sistema exibe as informações da forma de pagamento (PIX, BOLETO, CARTÃO DE CRÉDITO/DÉBITO, DINHEIRO).
   - e.	Prosseguir no passo 5 do fluxo principal
- **Fluxo de Exceção (5):** O aluno escolheu a opção de boleto.
   - a.	O sistema aguardará até o pagamento ser finalizado.
   - b.	Prosseguir para o passo 7 do fluxo principal depois da aprovação do boleto.
- **Fluxo de Exceção (5):** As credenciais do pagamento incorreto.
   - a.	Se o aluno possuir outra forma de pagamento, prosseguir no passo 4 do fluxo principal.

**Pós-condições:**
- O sistema registrou o pagamento com sucesso.
- O aluno receberá acesso aos recursos da academia.
- O sistema atualizará o status financeiro do aluno.

---

**Identificador:** UC -

**Nome:** Agendar Avaliação Técnica

**Objetivo:** Permitir que o aluno possa agendar sua avaliação técnica e visualizar no sistema.

**Atores:**
- Primário: Aluno
- Secundário: Sistema, Professor

**Pré-condições:**
- O aluno deve estar cadastrado no sistema.
- O professor deve estar cadastrado no sistema com o seu horário de trabalho definido.

**Cenários:**
- **Fluxo Principal:**
   1.	O aluno acessa o sistema (app/site) com credenciais validas.
   2.	O aluno abre a funcionalidade de “Agendar Avaliação Técnica”.
   3.	O sistema exibe os professes disponíveis, seus horários e datas.
   4.	O aluno seleciona o professor, horário e data disponível.
   5.	O sistema confirma o agendamento e notifica o professor.
   6.	No dia marcado, o aluno comparece na academia para a avaliação técnica.
   7.	O sistema mostra para o professor os alunos que tem para a avaliação do dia.
   8.	O professor seleciona o aluno e insere as informações das medidas no sistema.
   9.	O sistema registra as medições e atualiza no histórico.
   10. O aluno pode visualizar a avaliação pelo app/site
- **Fluxo Alternativo (3):** Não encontra professor disponível.
   - a.	O sistema envia uma mensagem ao aluno que não possui horário no momento
- **Fluxo de Exceção (5):** O sistema verifica novamente e não há disponibilidade.
   - a.	O sistema envia uma mensagem de indisponibilidade do professor.
   - b.	Prosseguir para o passo 3 do Fluxo Principal.
- **Fluxo de Exceção (6):** O aluno não compareceu na avaliação.
   - a.	O sistema registra o não comparecimento, caso tenha motivo, registrar o motivo e mantém o histórico atualizado para controle.
- **Fluxo de Exceção (2):** O aluno cancela a avaliação.
   - a.	Caso o aluno possui avaliação, o sistema exibirá somente a avaliação e não permitirá que marque uma avaliação.
   - b.	O aluno cancela a avaliação.

**Pós-condições:**
- Os resultados da avaliação técnica são registrados e vinculados com o histórico do aluno.
- O professor tem controle das avaliações realizadas para futuras análises.

### Diagrama de Atividades
![Diagrama de Atividades](./Diagramas/Diagrama%20de%20Atividades.jpg)

### Diagrama de Classes
![Diagrama de Classes](./Diagramas/Diagrama%20de%20Classes.jpg)

### Diagrama de Máquina de Estado
![Diagrama de Máquina de Estado-01](./Diagramas/Diagrama%20de%20Máquina%20de%20Estado-01.jpg)

![Diagrama de Máquina de Estado-02](./Diagramas/Diagrama%20de%20Máquina%20de%20Estado-02.jpg)

![Diagrama de Máquina de Estado-03](./Diagramas/Diagrama%20de%20Máquina%20de%20Estado-03.jpg)

![Diagrama de Máquina de Estado-04](./Diagramas/Diagrama%20de%20Máquina%20de%20Estado-04.jpg)