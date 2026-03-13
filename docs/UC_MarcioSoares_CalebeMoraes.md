# Entrega – Documento de Casos de Uso e Diagramas

## Identificação da Dupla
- Aluno 1: Marcio Soares
- Aluno 2: Calebe Moraes

## Arquivos Entregues

### Documento de Casos de Uso
Nome do arquivo entregue: UC_MarcioSoares_CalebeMoraes.md

### Diagramas de Casos de Uso
Arquivos entregues (PNG): 
- DUC_01_MarcioSoares_CalebeMoraes.png
- DUC_02_MarcioSoares_CalebeMoraes.png
- DUC_03_MarcioSoares_CalebeMoraes.png
- DUC_04_MarcioSoares_CalebeMoraes.png
- DUC_05_MarcioSoares_CalebeMoraes.png
- DUC_06_MarcioSoares_CalebeMoraes.png

## Issues Relacionadas
- Relacionado à Issue **#1 – Documento de Casos de Uso**
- Relacionado à Issue **#2 – Diagrama de Casos de Uso**

## Checklist Antes do Envio

- [x] O documento contém **20 casos de uso completos**, seguindo o template do arquivo `/docs/casosdeuso.md`
- [x] O nome do arquivo segue o padrão exigido
- [x] Os diagramas representam **todos os casos de uso listados** no documento
- [x] Todos os diagramas estão em **formato PNG**
- [x] As Issues foram referenciadas corretamente
- [x] O PR contém **apenas** os arquivos exigidos

---

## UC01 — Realizar Login

### Ator Principal
Aluno, Recepcionista, Instrutor, Gerente

### Objetivo
Permitir que o usuário acesse o sistema de acordo com seu perfil.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso e menu correspondente ao perfil carregado.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais e o perfil do usuário.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos
- **A1 — Senha incorreta:** O sistema exibe mensagem de erro e solicita nova tentativa.
- **A2 — Conta bloqueada/inativa:** O sistema impede o login e instrui o usuário a contatar a recepção.

### RF Relacionados
- N/A

### RNF Relacionados
- RNF02, RNF04

### RN Relacionadas
- RN06

---

## UC02 — Cadastrar Novo Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno na base de dados da academia.

### Pré-condições
- Recepcionista deve estar logado no sistema.

### Pós-condições
- Aluno cadastrado no sistema com dados pessoais e pronto para contratação de plano.

### Fluxo Principal
1. A recepcionista acessa a tela de cadastro de alunos.
2. Preenche os dados pessoais, contato e endereço.
3. O sistema valida as informações e salva o registro.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:** O sistema avisa que o aluno já existe e sugere ir para a tela de atualização.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02, RNF04

### RN Relacionadas
- RN06

---

## UC03 — Editar Dados do Aluno

### Ator Principal
Recepcionista

### Objetivo
Atualizar informações pessoais, de contato ou endereço de um aluno.

### Pré-condições
- O aluno deve estar previamente cadastrado.

### Pós-condições
- Os dados do aluno são atualizados no banco de dados.

### Fluxo Principal
1. A recepcionista busca o aluno pelo nome ou CPF.
2. Altera os dados necessários (ex: novo telefone).
3. O sistema salva as alterações e exibe mensagem de sucesso.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:** O sistema exibe mensagem informando que a busca não retornou resultados.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN06

---

## UC04 — Cadastrar Plano

### Ator Principal
Gerente

### Objetivo
Criar um novo tipo de plano (mensal, anual, etc.) para comercialização.

### Pré-condições
- Gerente deve estar logado no sistema.

### Pós-condições
- Novo plano disponível para atribuição a alunos.

### Fluxo Principal
1. O gerente acessa a gestão de planos e seleciona "Novo Plano".
2. Define nome, duração, valor e modalidades inclusas.
3. O sistema salva e ativa o plano no catálogo.

### Fluxos Alternativos
- **A1 — Dados incompletos:** O sistema bloqueia o salvamento e destaca os campos obrigatórios.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

---

## UC05 — Editar/Desativar Plano

### Ator Principal
Gerente

### Objetivo
Alterar valores de um plano existente ou desativá-lo para não ser mais vendido.

### Pré-condições
- O plano deve existir no sistema.

### Pós-condições
- Plano atualizado ou desativado do catálogo de vendas.

### Fluxo Principal
1. O gerente lista os planos cadastrados e seleciona um.
2. Altera os parâmetros desejados ou marca como "Inativo".
3. O sistema salva as alterações.

### Fluxos Alternativos
- **A1 — Plano com alunos ativos:** Se for inativado, o sistema avisa que os alunos atuais continuam com acesso até o fim do contrato vigente.

### RF Relacionados
- RF02

### RNF Relacionados
- N/A

### RN Relacionadas
- RN06

---

## UC06 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade feito fisicamente na academia.

### Pré-condições
- Aluno deve estar cadastrado e com plano atribuído.

### Pós-condições
- Pagamento registrado e regularidade do aluno atualizada.

### Fluxo Principal
1. A recepcionista localiza o aluno e acessa a fatura pendente.
2. Seleciona o método de pagamento (dinheiro, cartão ou PIX).
3. Confirma o recebimento do valor integral.
4. O sistema registra o pagamento e atualiza a situação do aluno.

### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:** O sistema bloqueia a transação, pois o valor deve ser integral.

### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN04, RN06, RN07

---

## UC07 — Realizar Pagamento Online

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno pague sua mensalidade pelo sistema web/mobile.

### Pré-condições
- Aluno logado e com fatura em aberto.

### Pós-condições
- Pagamento processado e regularidade atualizada automaticamente.

### Fluxo Principal
1. O aluno acessa a área financeira.
2. Seleciona a fatura em aberto e escolhe Cartão de Crédito ou PIX.
3. Realiza o pagamento através da integração com o gateway.
4. O sistema confirma a transação e atualiza o status para regular.

### Fluxos Alternativos
- **A1 — Pagamento recusado:** O sistema notifica o aluno da recusa e mantém a fatura em aberto.

### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF02, RNF03

### RN Relacionadas
- RN04, RN07

---

## UC08 — Validar Acesso via Catraca (RFID)

### Ator Principal
Sistema de Catraca

### Objetivo
Liberar ou bloquear a entrada do aluno fisicamente na academia.

### Pré-condições
- O aluno deve aproximar sua tag RFID/Biometria da catraca.

### Pós-condições
- Catraca liberada ou bloqueada, com registro de log no sistema.

### Fluxo Principal
1. O Sistema de Catraca envia o ID do aluno via API para o sistema FitPass.
2. O sistema FitPass verifica a regularidade do aluno.
3. Sendo regular, retorna status de "Liberado".
4. O Sistema de Catraca libera a roleta e o FitPass registra o histórico de acesso.

### Fluxos Alternativos
- **A1 — Mensalidade vencida há > 5 dias:** O FitPass retorna "Bloqueado" e a catraca não abre.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF03, RNF06

### RN Relacionadas
- RN01

---

## UC09 — Visualizar Horários de Aulas

### Ator Principal
Aluno

### Objetivo
Consultar a grade de aulas disponíveis na academia.

### Pré-condições
- Aluno logado no sistema.

### Pós-condições
- Grade de aulas exibida com horários, instrutores e vagas disponíveis.

### Fluxo Principal
1. O aluno acessa a aba "Grade de Aulas".
2. O sistema exibe o calendário semanal com as aulas.
3. O aluno pode filtrar por modalidade.

### Fluxos Alternativos
- **A1 — Nenhuma aula agendada:** O sistema exibe mensagem de que não há turmas para o filtro selecionado.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- N/A

---

## UC10 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula específica.

### Pré-condições
- Aluno logado, situação regular e aula com vagas abertas.

### Pós-condições
- Vaga reservada para o aluno e notificação de confirmação enviada.

### Fluxo Principal
1. Na grade de horários, o aluno clica em "Agendar" na aula desejada.
2. O sistema verifica se há vagas disponíveis.
3. O sistema confirma o agendamento e reduz o número de vagas.
4. O sistema envia notificação de confirmação ao aluno.

### Fluxos Alternativos
- **A1 — Limite de vagas atingido:** O botão de agendar fica bloqueado e o sistema informa que a turma está lotada.

### RF Relacionados
- RF06, RF10

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN02

---

## UC11 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Cancelar uma reserva feita previamente.

### Pré-condições
- Aluno deve ter um agendamento ativo.

### Pós-condições
- Vaga liberada no sistema para outros alunos.

### Fluxo Principal
1. O aluno acessa "Meus Agendamentos".
2. Clica em "Cancelar" na aula desejada.
3. O sistema verifica a antecedência (maior que 1 hora).
4. O sistema processa o cancelamento e devolve a vaga para a turma.

### Fluxos Alternativos
- **A1 — Cancelamento com menos de 1 hora:** O sistema impede a ação e informa a regra de cancelamento.

### RF Relacionados
- RF06

### RNF Relacionados
- N/A

### RN Relacionadas
- RN03

---

## UC12 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Confirmar quais alunos agendados compareceram à aula.

### Pré-condições
- Instrutor logado e aula prestes a iniciar ou recém-finalizada.

### Pós-condições
- Presença dos alunos registrada no banco de dados.

### Fluxo Principal
1. O instrutor acessa a aula específica no sistema.
2. O sistema lista todos os alunos que agendaram a aula.
3. O instrutor marca "Presente" ou "Falta" para cada um.
4. O sistema salva a lista de presença.

### Fluxos Alternativos
- **A1 — Aluno não agendado quer participar:** Se houver vaga, o instrutor pode adicionar o aluno manualmente à lista de presença na hora.

### RF Relacionados
- RF07

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

---

## UC13 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Inserir métricas e documentos de avaliação física do aluno.

### Pré-condições
- Instrutor logado; aluno deve estar ativo e regular.

### Pós-condições
- Avaliação salva e notificação de liberação enviada ao aluno.

### Fluxo Principal
1. O instrutor seleciona o aluno e clica em "Nova Avaliação".
2. O sistema verifica a regularidade do aluno.
3. O instrutor insere peso, IMC, percentual de gordura e anexa arquivos (ex: bioimpedância).
4. O sistema salva os dados e dispara notificação ao aluno informando que a avaliação está disponível.

### Fluxos Alternativos
- **A1 — Aluno irregular:** O sistema bloqueia a criação da avaliação e avisa o instrutor.

### RF Relacionados
- RF08, RF10

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN05, RN06

---

## UC14 — Visualizar Avaliação Física

### Ator Principal
Aluno

### Objetivo
Acessar os resultados de suas avaliações físicas.

### Pré-condições
- Aluno logado e com avaliação já registrada pelo instrutor.

### Pós-condições
- Dados e anexos da avaliação exibidos em tela.

### Fluxo Principal
1. O aluno acessa o menu "Minhas Avaliações".
2. O sistema lista o histórico de avaliações por data.
3. O aluno seleciona uma avaliação para ver os detalhes e baixar anexos.

### Fluxos Alternativos
- **A1 — Nenhuma avaliação cadastrada:** O sistema exibe mensagem orientando a procurar um instrutor.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF02 (Dados sensíveis e de saúde protegidos)

### RN Relacionadas
- N/A

---

## UC15 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Visualizar lista de alunos com pagamentos atrasados.

### Pré-condições
- Gerente logado no sistema.

### Pós-condições
- Relatório gerado em tela com opção de exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. Seleciona "Relatório de Inadimplência".
3. O sistema compila e exibe a lista de alunos com faturas vencidas, ordenados por dias de atraso.

### Fluxos Alternativos
- **A1 — Nenhum inadimplente:** O sistema informa que todos os alunos estão regulares.

### RF Relacionados
- RF09

### RNF Relacionados
- N/A

### RN Relacionadas
- RN06

---

## UC16 — Emitir Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Acompanhar o total de alunos ativos divididos por planos.

### Pré-condições
- Gerente logado no sistema.

### Pós-condições
- Relatório quantitativo e qualitativo exibido.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios e seleciona "Alunos Ativos".
2. O sistema busca os dados e apresenta um consolidado com totais e agrupamento por tipo de plano contratado.

### Fluxos Alternativos
- N/A

### RF Relacionados
- RF09

### RNF Relacionados
- N/A

### RN Relacionadas
- RN06

---

## UC17 — Emitir Relatório de Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Auditar os horários de pico e entrada de alunos via catraca.

### Pré-condições
- Gerente logado no sistema.

### Pós-condições
- Listagem e gráficos de acessos gerados.

### Fluxo Principal
1. O gerente seleciona "Histórico de Acessos".
2. Informa um período de datas.
3. O sistema gera a relação de entradas validadas e bloqueadas pela catraca no período informado.

### Fluxos Alternativos
- **A1 — Período sem registros:** O sistema exibe relatório em branco com aviso.

### RF Relacionados
- RF09

### RNF Relacionados
- N/A

### RN Relacionadas
- RN06

---

## UC18 — Emitir Relatório de Ocupação das Aulas

### Ator Principal
Gerente

### Objetivo
Analisar quais aulas/modalidades estão mais cheias ou vazias.

### Pré-condições
- Gerente logado no sistema.

### Pós-condições
- Relatório de ocupação percentual e quantitativa gerado.

### Fluxo Principal
1. O gerente seleciona "Ocupação das Aulas".
2. Informa o mês ou semana desejada.
3. O sistema cruza os dados de agendamentos com as presenças registradas e exibe a taxa de ocupação de cada turma.

### Fluxos Alternativos
- N/A

### RF Relacionados
- RF09

### RNF Relacionados
- N/A

### RN Relacionadas
- RN06

---

## UC19 — Enviar Notificação de Vencimento

### Ator Principal
Sistema (Tempo / Processo Batch)

### Objetivo
Avisar os alunos preventivamente sobre o vencimento de suas mensalidades.

### Pré-condições
- A fatura do aluno deve estar a 'x' dias do vencimento (ex: 3 dias antes).

### Pós-condições
- E-mail/Push notification enviado para o aluno.

### Fluxo Principal
1. Diariamente, o sistema varre o banco de dados buscando faturas próximas do vencimento.
2. Identifica os alunos correspondentes.
3. Dispara as mensagens de notificação padronizadas com o link para pagamento.

### Fluxos Alternativos
- N/A

### RF Relacionados
- RF10

### RNF Relacionados
- N/A

### RN Relacionadas
- N/A

---

## UC20 — Atualizar Status de Regularidade Automática

### Ator Principal
Sistema (Trigger Financeiro)

### Objetivo
Modificar o status do aluno (regular/inadimplente) automaticamente com o passar dos dias ou compensação financeira.

### Pré-condições
- Fatura atingir 6 dias de atraso ou pagamento ser confirmado.

### Pós-condições
- Perfil do aluno bloqueado ou liberado para catraca/agendamentos.

### Fluxo Principal
1. O sistema recebe a confirmação de um pagamento (baixa automática) OU identifica via rotina diária que uma fatura passou de 5 dias de atraso.
2. O sistema altera o campo de regularidade no perfil do aluno correspondente.
3. A alteração reflete instantaneamente para a API da catraca e tela de agendamento.

### Fluxos Alternativos
- N/A

### RF Relacionados
- RF04

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN01, RN07