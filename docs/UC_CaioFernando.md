# Documento de Casos de Uso – FitPass Gym Management

**Autor:** Caio Fernando
**Projeto:** Estudo de Caso FitPass – Engenharia de Software

---

## UC01 — Realizar Login
### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor ou Gerente)
### Objetivo
Permitir que o usuário acesse as funcionalidades do sistema de acordo com seu perfil.
### Pré-condições
- Usuário deve possuir cadastro ativo no banco de dados.
### Pós-condições
- Sessão iniciada e redirecionamento para o painel principal.
### Fluxo Principal
1. O usuário informa seu CPF e senha.
2. O sistema valida as credenciais contra a base de dados.
3. O sistema autentica o usuário e libera o acesso.
### Fluxos Alternativos
- **A1 — Credenciais Incorretas:** O sistema exibe mensagem de erro e solicita nova tentativa.
### RF Relacionados: RF01 | RNF Relacionados: RNF01 | RN Relacionadas: RN01

---

## UC02 — Realizar Matrícula de Aluno
### Ator Principal
Recepcionista
### Objetivo
Cadastrar um novo aluno no sistema e vincular a um plano.
### Pré-condições
- Recepcionista logado no sistema.
### Pós-condições
- Novo registro de aluno criado com status "Ativo".
### Fluxo Principal
1. O recepcionista acessa o menu "Matrículas".
2. Informa dados pessoais (Nome, CPF, Data de Nascimento, E-mail).
3. Seleciona o plano de academia desejado.
4. O sistema confirma o cadastro e gera o primeiro título financeiro.
### Fluxos Alternativos
- **A1 — CPF já cadastrado:** O sistema impede a operação e mostra o perfil existente.
### RF Relacionados: RF02 | RN Relacionadas: RN02

---

## UC03 — Cadastrar Plano
### Ator Principal
Gerente
### Objetivo
Criar modalidades de planos (Ex: Mensal, Trimestral, VIP).
### Pré-condições
- Usuário logado com perfil de Gerente.
### Pós-condições
- Novo plano disponível para venda na recepção.
### Fluxo Principal
1. O gerente define o nome do plano, valor, duração e benefícios.
2. O sistema salva as configurações.
### RF Relacionados: RF03

---

## UC04 — Registrar Pagamento de Mensalidade
### Ator Principal
Recepcionista
### Objetivo
Dar baixa em parcelas financeiras e atualizar o status do aluno.
### Pré-condições
- Aluno possuir uma conta a pagar no sistema.
### Pós-condições
- Parcela marcada como "Paga" e recibo gerado.
### Fluxo Principal
1. O recepcionista localiza o aluno pelo nome ou CPF.
2. Seleciona a parcela em aberto e a forma de pagamento.
3. O sistema confirma a transação e atualiza a situação financeira.
### RF Relacionados: RF04 | RN Relacionadas: RN03

---

## UC05 — Validar Acesso via Catraca
### Ator Principal
Aluno / Sistema de Catraca (API)
### Objetivo
Controlar a entrada física dos alunos na unidade.
### Pré-condições
- Aluno deve possuir tag RFID ou Biometria cadastrada.
### Pós-condições
- Acesso liberado fisicamente.
### Fluxo Principal
1. O aluno identifica-se na catraca.
2. O sistema verifica se o plano está ativo e o pagamento em dia.
3. O sistema envia o comando de liberação para a trava física.
### Fluxos Alternativos
- **A1 — Inadimplente:** O sistema bloqueia a entrada e exibe alerta para procurar a recepção.
### RF Relacionados: RF05 | RN Relacionadas: RN04

---

## UC06 — Agendar Aula Coletiva
### Ator Principal
Aluno
### Objetivo
Reservar vaga em modalidades com limite de pessoas (Ex: Crossfit, Dança).
### Pré-condições
- Aluno logado no aplicativo mobile.
### Pós-condições
- Vaga reservada para o aluno na lista da aula.
### Fluxo Principal
1. O aluno escolhe a modalidade e o horário no calendário.
2. O sistema valida se há vagas disponíveis.
3. O sistema confirma o agendamento.
### Fluxos Alternativos
- **A1 — Sem vagas:** O sistema oferece opção de entrar na lista de espera.
### RF Relacionados: RF06 | RN Relacionadas: RN05

---

## UC07 — Cancelar Agendamento
### Ator Principal
Aluno
### Objetivo
Liberar vaga em aula previamente reservada.
### Pré-condições
- Possuir agendamento ativo.
### Fluxo Principal
1. O aluno acessa seus agendamentos e clica em cancelar.
2. O sistema remove a reserva e notifica o próximo da lista de espera.
### RF Relacionados: RF07 | RN Relacionadas: RN06

---

## UC08 — Registrar Presença em Aula
### Ator Principal
Instrutor
### Objetivo
Validar o comparecimento dos alunos agendados.
### Pré-condições
- Instrutor logado e aula em horário de início.
### Fluxo Principal
1. O instrutor abre a chamada digital da aula.
2. Marca a presença para os alunos que compareceram.
3. O sistema salva os dados para estatísticas de frequência.
### RF Relacionados: RF08

---

## UC09 — Realizar Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Registrar medidas e índices corporais do aluno.
### Pré-condições
- Selecionar aluno cadastrado.
### Pós-condições
- Relatório de evolução disponível no perfil do aluno.
### Fluxo Principal
1. O instrutor insere peso, altura e percentual de gordura.
2. O sistema calcula automaticamente o IMC e dobras cutâneas.
3. O sistema salva a avaliação.
### RF Relacionados: RF09

---

## UC10 — Consultar Ficha de Treino
### Ator Principal
Aluno
### Objetivo
Orientar o aluno sobre os exercícios do dia.
### Pré-condições
- Treino deve ter sido montado por um instrutor.
### Fluxo Principal
1. O aluno abre a seção "Treinos" no aplicativo.
2. O sistema exibe a lista de exercícios, séries e cargas.
### RF Relacionados: RF10

---

## UC11 — Montar Ficha de Treino
### Ator Principal
Instrutor
### Objetivo
Prescrever a rotina de exercícios para o aluno.
### Pré-condições
- Instrutor logado.
### Fluxo Principal
1. O instrutor seleciona o perfil do aluno.
2. Adiciona os exercícios da biblioteca padrão.
3. Define as repetições e períodos de descanso.
4. Salva a ficha para visualização imediata do aluno.
### RF Relacionados: RF11

---

## UC12 — Gerar Relatório Gerencial
### Ator Principal
Gerente
### Objetivo
Visualizar a saúde financeira e operacional da academia.
### Pré-condições
- Perfil administrativo.
### Fluxo Principal
1. O gerente seleciona o período (Ex: Janeiro/2026).
2. O sistema compila total de matrículas, cancelamentos e faturamento.
3. O relatório é exibido na tela ou exportado para PDF.
### RF Relacionados: RF12

---

## UC13 — Registrar Saída na Catraca
### Ator Principal
Aluno
### Objetivo
Registrar o fim da sessão de treino para controle de fluxo.
### Pré-condições
- Registro de entrada ativo.
### Fluxo Principal
1. O aluno aciona a catraca de saída.
2. O sistema encerra o registro de permanência e libera o giro.
### RF Relacionados: RF13

---

## UC14 — Aplicar Desconto
### Ator Principal
Gerente
### Objetivo
Ajustar o valor de mensalidades por motivos promocionais ou de retenção.
### Pré-condições
- Gerente logado.
### Fluxo Principal
1. O gerente acessa o financeiro de um aluno específico.
2. Insere o valor ou percentual de desconto.
3. O sistema recalcula o valor final da fatura.
### RF Relacionados: RF14 | RN Relacionadas: RN07

---

## UC15 — Bloquear Acesso Administrativo
### Ator Principal
Recepcionista
### Objetivo
Impedir o acesso de alunos por motivos não financeiros (Ex: Comportamento).
### Pré-condições
- Aluno com cadastro ativo.
### Fluxo Principal
1. O recepcionista altera o status do aluno para "Bloqueado".
2. O sistema impede imediatamente a entrada na catraca.
### RF Relacionados: RF15

---

## UC16 — Cadastrar Novo Exercício
### Ator Principal
Instrutor
### Objetivo
Expandir a biblioteca de exercícios disponíveis para treino.
### Pré-condições
- Instrutor logado.
### Fluxo Principal
1. O instrutor insere o nome do exercício e o grupamento muscular.
2. O sistema salva na base global de exercícios.
### RF Relacionados: RF16

---

## UC17 — Emitir Recibo de Pagamento
### Ator Principal
Recepcionista
### Objetivo
Fornecer comprovante de transação financeira ao aluno.
### Pré-condições
- Pagamento registrado no UC04.
### Fluxo Principal
1. O recepcionista seleciona "Emitir Recibo" após o pagamento.
2. O sistema gera um documento PDF com os dados da transação.
### RF Relacionados: RF17

---

## UC18 — Consultar Histórico de Presença
### Ator Principal
Aluno
### Objetivo
Permitir que o aluno acompanhe sua frequência.
### Pré-condições
- Aluno logado no App.
### Fluxo Principal
1. O aluno acessa o menu "Frequência".
2. O sistema exibe um calendário com os dias em que houve entrada via catraca.
### RF Relacionados: RF18

---

## UC19 — Trancar Matrícula
### Ator Principal
Recepcionista
### Objetivo
Pausar o plano do aluno por um período determinado.
### Pré-condições
- Aluno sem débitos pendentes.
### Fluxo Principal
1. O recepcionista define a data de início e término do trancamento.
2. O sistema suspende os acessos e interrompe a geração de novas cobranças.
### RF Relacionados: RF19 | RN Relacionadas: RN08

---

## UC20 — Redefinir Senha
### Ator Principal
Usuário
### Objetivo
Recuperar o acesso ao sistema em caso de esquecimento de senha.
### Pré-condições
- Usuário deve possuir um e-mail válido no cadastro.
### Fluxo Principal
1. O usuário clica em "Esqueci minha senha" na tela de login.
2. O sistema envia um código de verificação para o e-mail.
3. O usuário digita o código e cadastra uma nova senha.
### RF Relacionados: RF20
