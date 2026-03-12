### UC01 — Realizar Login
### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)
### Objetivo
Permitir que o usuário acesse o sistema.
### Pré-condições
- Usuário deve possuir cadastro ativo.
### Pós-condições
- Sessão iniciada com sucesso.
### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.
### Fluxos Alternativos
- **A1 — Senha incorreta:** O sistema exibe mensagem de erro.
- **A2 — Conta bloqueada:** O sistema impede o login e instrui o usuário a recuperar o acesso.
### RF Relacionados
- RF01
### RNF Relacionados
- RNF01
### RN Relacionadas
- RN01

---

### UC02 — Cadastrar Aluno
### Ator Principal
Recepcionista
### Objetivo
Registrar um novo aluno no sistema.
### Pré-condições
- Recepcionista autenticado.
### Pós-condições
- Cadastro do aluno salvo no banco de dados.
### Fluxo Principal
1. O recepcionista solicita a criação de um novo cadastro.
2. O sistema apresenta o formulário de dados pessoais.
3. O recepcionista preenche nome, CPF, e-mail e telefone.
4. O sistema valida os dados e confirma o cadastro.
### Fluxos Alternativos
- **A1 — CPF Inválido:** O sistema emite alerta e impede a gravação.
### RF Relacionados
- RF02
### RN Relacionadas
- RN02

---

### UC03 — Matricular em Plano
### Ator Principal
Recepcionista
### Objetivo
Vincular um aluno a um plano de pagamento e acesso.
### Pré-condições
- Aluno cadastrado; Planos configurados no sistema.
### Pós-condições
- Matrícula ativa gerada.
### Fluxo Principal
1. O recepcionista busca o aluno pelo nome ou CPF.
2. O sistema exibe os planos disponíveis.
3. O recepcionista seleciona o plano (Mensal, Trimestral ou Anual).
4. O sistema gera o contrato e a primeira cobrança.
### RF Relacionados
- RF03
### RN Relacionadas
- RN03

---

### UC04 — Gerenciar Planos
### Ator Principal
Gerente
### Objetivo
Criar ou editar modalidades de planos e valores.
### Pré-condições
- Acesso de nível gerencial.
### Pós-condições
- Tabela de preços e planos atualizada.
### Fluxo Principal
1. O gerente acessa o menu de configurações de planos.
2. O sistema lista os planos existentes.
3. O gerente altera valores ou cria um novo plano com descrição de benefícios.
4. O sistema salva as alterações.
### RF Relacionados
- RF04
### RN Relacionadas
- RN04

---

### UC05 — Registrar Pagamento
### Ator Principal
Recepcionista
### Objetivo
Dar baixa em mensalidades pagas pelo aluno.
### Pré-condições
- Aluno com fatura em aberto.
### Pós-condições
- Status da fatura alterado para "Pago".
### Fluxo Principal
1. O recepcionista localiza a pendência financeira do aluno.
2. O sistema exibe o valor total com possíveis multas.
3. O recepcionista seleciona o método de pagamento (Dinheiro, Cartão ou PIX).
4. O sistema confirma a transação e gera o recibo.
### RF Relacionados
- RF05
### RN Relacionadas
- RN05

---

### UC06 — Controlar Acesso (Catraca)
### Ator Principal
Sistema de Catraca (API)
### Objetivo
Validar a entrada do aluno via RFID.
### Pré-condições
- Aluno aproximar tag/cartão na catraca.
### Pós-condições
- Log de acesso registrado; Catraca liberada ou travada.
### Fluxo Principal
1. A API da catraca envia o ID do RFID para o servidor.
2. O sistema verifica se o aluno tem plano ativo e está adimplente.
3. O sistema retorna o comando de liberação.
### Fluxos Alternativos
- **A1 — Inadimplência:** O sistema bloqueia a entrada e orienta procurar a recepção.
### RF Relacionados
- RF06
### RN Relacionadas
- RN06

---

### UC07 — Agendar Aula Coletiva
### Ator Principal
Aluno
### Objetivo
Reservar vaga em aulas de horários fixos.
### Pré-condições
- Aluno logado no app; Plano ativo.
### Pós-condições
- Reserva confirmada na lista da aula.
### Fluxo Principal
1. O aluno acessa a grade de horários no app.
2. O sistema exibe as vagas disponíveis.
3. O aluno clica em "Agendar".
4. O sistema confirma a vaga.
### Fluxos Alternativos
- **A1 — Limite de vagas atingido:** O sistema oferece lista de espera.
### RF Relacionados
- RF07

---

### UC08 — Registrar Presença em Aula
### Ator Principal
Instrutor
### Objetivo
Confirmar o comparecimento dos alunos na aula.
### Pré-condições
- Aula em andamento ou finalizada.
### Pós-condições
- Status de presença atualizado para os alunos agendados.
### Fluxo Principal
1. O instrutor acessa a lista de agendamento da aula específica.
2. O sistema lista os nomes dos alunos.
3. O instrutor marca os alunos presentes.
4. O sistema salva o registro de frequência.
### RF Relacionados
- RF08

---

### UC09 — Realizar Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Coletar dados antropométricos do aluno.
### Pré-condições
- Aluno com horário marcado para avaliação.
### Pós-condições
- Laudo de avaliação gerado no perfil do aluno.
### Fluxo Principal
1. O instrutor seleciona o aluno no sistema.
2. O sistema abre o formulário de avaliação (peso, medidas, dobras).
3. O instrutor preenche os campos e confirma.
4. O sistema calcula o IMC e percentuais, salvando o resultado.
### RF Relacionados
- RF09

---

### UC10 — Prescrever Treino
### Ator Principal
Instrutor
### Objetivo
Montar a ficha de exercícios personalizada para o aluno.
### Pré-condições
- Aluno cadastrado.
### Pós-condições
- Ficha de treino disponível no app do aluno.
### Fluxo Principal
1. O instrutor acessa o perfil do aluno e seleciona "Novo Treino".
2. O sistema abre a biblioteca de exercícios.
3. O instrutor define séries, repetições e cargas.
4. O sistema salva o treino com data de expiração.
### RF Relacionados
- RF10

---

### UC11 — Consultar Treino
### Ator Principal
Aluno
### Objetivo
Visualizar os exercícios a serem realizados no dia.
### Pré-condições
- Treino prescrito pelo instrutor.
### Pós-condições
- Exibição dos dados do treino.
### Fluxo Principal
1. O aluno abre o aplicativo.
2. O sistema identifica o dia da semana e o treino correspondente (ex: Treino A).
3. O aluno visualiza a lista de exercícios e observações do instrutor.
### RF Relacionados
- RF11

---

### UC12 — Gerar Relatório de Faturamento
### Ator Principal
Gerente
### Objetivo
Analisar as receitas da academia em determinado período.
### Pré-condições
- Acesso gerencial.
### Pós-condições
- Relatório em tela ou PDF gerado.
### Fluxo Principal
1. O gerente acessa o menu "Relatórios".
2. O sistema solicita o período inicial e final.
3. O gerente confirma a busca.
4. O sistema consolida todos os pagamentos recebidos no intervalo.
### RF Relacionados
- RF12

---

### UC13 — Cancelar Matrícula
### Ator Principal
Recepcionista
### Objetivo
Encerrar o vínculo contratual de um aluno.
### Pré-condições
- Aluno com matrícula ativa.
### Pós-condições
- Matrícula inativada; Acesso bloqueado.
### Fluxo Principal
1. O recepcionista busca o aluno.
2. O sistema exibe o status da matrícula e possíveis multas de rescisão.
3. O recepcionista confirma o cancelamento.
4. O sistema atualiza o status para "Inativo".
### RF Relacionados
- RF13
### RN Relacionadas
- RN07

---

### UC14 — Emitir Aviso de Inadimplência
### Ator Principal
Gerente
### Objetivo
Notificar alunos com mensalidades atrasadas.
### Pré-condições
- Existência de faturas vencidas.
### Pós-condições
- Notificação (E-mail/Push) enviada ao aluno.
### Fluxo Principal
1. O gerente solicita a listagem de inadimplentes.
2. O sistema filtra todos os alunos com débitos > 5 dias.
3. O gerente clica em "Notificar Todos".
4. O sistema envia as comunicações automaticamente.
### RF Relacionados
- RF14

---

### UC15 — Consultar Histórico de Acessos
### Ator Principal
Gerente
### Objetivo
Verificar o fluxo de pessoas na academia.
### Pré-condições
- Registros de catraca existentes.
### Pós-condições
- Lista de acessos exibida.
### Fluxo Principal
1. O gerente seleciona a opção "Histórico de Acesso".
2. O sistema permite filtrar por aluno ou por data.
3. O sistema exibe horários de entrada e saída.
### RF Relacionados
- RF15

---

### UC16 — Gerenciar Cadastro de Instrutores
### Ator Principal
Gerente
### Objetivo
Admitir ou editar dados de funcionários técnicos.
### Pré-condições
- Acesso gerencial.
### Pós-condições
- Instrutor habilitado para prescrever treinos.
### Fluxo Principal
1. O gerente acessa "Gestão de Equipe".
2. O sistema apresenta formulário para CREF, especialidades e horários.
3. O gerente salva o cadastro.
4. O sistema gera credenciais de acesso para o instrutor.
### RF Relacionados
- RF16

---

### UC17 — Trancar Matrícula
### Ator Principal
Recepcionista
### Objetivo
Suspender temporariamente o plano do aluno.
### Pré-condições
- Aluno em dia com as mensalidades.
### Pós-condições
- Período de validade do plano prorrogado; Acesso suspenso.
### Fluxo Principal
1. O recepcionista acessa a matrícula do aluno.
2. O sistema solicita o motivo e o prazo de trancamento.
3. O sistema valida se o plano permite essa ação.
4. O sistema confirma a pausa do contrato.
### RF Relacionados
- RF17
### RN Relacionadas
- RN08

---

### UC18 — Alterar Senha
### Ator Principal
Usuário
### Objetivo
Permitir a troca da credencial de segurança.
### Pré-condições
- Usuário logado ou com acesso ao e-mail cadastrado.
### Pós-condições
- Senha atualizada no sistema.
### Fluxo Principal
1. O usuário acessa "Meu Perfil".
2. O sistema solicita a senha atual e a nova senha (duas vezes).
3. O sistema valida a complexidade da nova senha.
4. O sistema confirma a alteração.
### RF Relacionados
- RF18

---

### UC19 — Visualizar Gráfico de Evolução
### Ator Principal
Aluno
### Objetivo
Acompanhar o progresso dos resultados físicos.
### Pré-condições
- Ter pelo menos duas avaliações físicas realizadas.
### Pós-condições
- Gráficos comparativos exibidos no app.
### Fluxo Principal
1. O aluno acessa a aba "Evolução" no aplicativo.
2. O sistema cruza os dados das avaliações anteriores.
3. O sistema gera gráficos de peso, gordura e massa magra.
### RF Relacionados
- RF19

---

### UC20 — Configurar Horários da Academia
### Ator Principal
Gerente
### Objetivo
Definir períodos de funcionamento e horários de pico.
### Pré-condições
- Acesso administrativo.
### Pós-condições
- Grade de funcionamento atualizada no sistema e app.
### Fluxo Principal
1. O gerente acessa "Configurações da Unidade".
2. O sistema exibe os horários de segunda a domingo.
3. O gerente altera os intervalos de abertura e fechamento.
4. O sistema replica a informação para os usuários.
### RF Relacionados
- RF20
