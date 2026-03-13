# Organograma do Sistema
---
![alt text](DUC_01_GustavoPomeranziLedesma_VitorHenriqueDaSilva.png)

---

# Documento de Casos de Uso - FitPass Gym Management

## UC01 — Realizar Login
### Ator Principal
Todos os Usuários
### Objetivo
Permitir que o usuário acesse o sistema com seu perfil específico.
### Pré-condições
- Usuário deve possuir cadastro e perfil ativo no sistema.
### Pós-condições
- Sessão iniciada com sucesso, apresentando o menu correspondente ao perfil.
### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.
### Fluxos Alternativos
- **A1 — Senha incorreta:** O sistema exibe mensagem de erro.
- **A2 — Conta bloqueada:** O sistema impede o login e exibe os passos para recuperação.
### RF Relacionados
- RF01
### RNF Relacionados
- RNF02, RNF04
### RN Relacionadas
- RN06

---

## UC02 — Cadastrar Novo Aluno
### Ator Principal
Recepcionista
### Objetivo
Registrar um novo aluno no sistema.
### Pré-condições
- O recepcionista deve estar autenticado e o CPF não pode estar cadastrado.
### Pós-condições
- Os dados do aluno são salvos e o contrato inicial é vinculado.
### Fluxo Principal
1. O recepcionista preenche dados pessoais, contato e endereço.
2. O recepcionista seleciona o plano desejado.
3. O sistema salva o cadastro e gera o registro de pagamento inicial.
### Fluxos Alternativos
- **A1 — CPF já cadastrado:** O sistema alerta que já existe um aluno com esse documento.
### RF Relacionados
- RF01
### RNF Relacionados
- RNF02, RNF04
### RN Relacionadas
- RN06

---

## UC03 — Criar Novo Plano
### Ator Principal
Gerente
### Objetivo
Criar e configurar modalidades de planos oferecidos pela academia.
### Pré-condições
- Estar autenticado como Gerente.
### Pós-condições
- Novo plano disponível para matrículas.
### Fluxo Principal
1. O gerente insere o nome, modalidade, preço e duração do plano.
2. O sistema valida as informações e permite salvar.
3. O plano fica disponível para seleção em novos cadastros.
### Fluxos Alternativos
- **A1 — Dados incompletos:** O sistema bloqueia a criação e marca os campos obrigatórios.
### RF Relacionados
- RF02
### RNF Relacionados
- RNF04
### RN Relacionadas
- RN06

---

## UC04 — Editar Plano Existente
### Ator Principal
Gerente
### Objetivo
Alterar informações de preço, duração ou modalidades de um plano.
### Pré-condições
- Estar logado com perfil Gerente e selecionar um plano.
### Pós-condições
- As informações do plano são atualizadas para futuras matrículas.
### Fluxo Principal
1. O Gerente acessa a lista de planos e seleciona "Editar".
2. Altera os valores desejados (ex: preço mensalidade).
3. O sistema salva as alterações no banco de dados.
### Fluxos Alternativos
- **A1 — Tentativa de exclusão de plano com alunos:** O sistema impede a exclusão mas permite "inativar" o plano.
### RF Relacionados
- RF02
### RNF Relacionados
- RNF04
### RN Relacionadas
- RN06

---

## UC05 — Registrar Pagamento na Recepção
### Ator Principal
Recepcionista
### Objetivo
Dar baixa na mensalidade ou débitos de um aluno presencialmente.
### Pré-condições
- O aluno precisa estar cadastrado e com pendências ou renovação.
### Pós-condições
- Mensalidade quitada, registro financeiro gravado e o aluno fica com status "Regular".
### Fluxo Principal
1. O recepcionista seleciona o aluno e a dívida.
2. Define a forma de pagamento (Dinheiro, Cartão, PIX).
3. Efetiva o pagamento.
4. O sistema atualiza o status de regularidade do aluno.
### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:** O sistema impede e exige o valor integral (RN04).
### RF Relacionados
- RF03, RF04
### RNF Relacionados
- RNF04
### RN Relacionadas
- RN04, RN06, RN07

---

## UC06 — Gerar Pagamento Online (Boleto/PIX)
### Ator Principal
Aluno
### Objetivo
Permitir que o aluno pague a mensalidade sem ir à recepção.
### Pré-condições
- O aluno precisa ter pendências e login no portal/app.
### Pós-condições
- Código de barras ou link PIX gerado.
### Fluxo Principal
1. O aluno acessa a aba Financeiro do app.
2. Seleciona a mensalidade e a opção "Pagar Online".
3. O sistema gera os dados para pagamento.
### Fluxos Alternativos
- **A1 — Sistema de pagamento indisponível:** O sistema exibe um aviso orientando a pagar na recepção.
### RF Relacionados
- RF03
### RNF Relacionados
- RNF01, RNF04
### RN Relacionadas
- RN04

---

## UC07 — Validar Regularidade do Aluno
### Ator Principal
Sistema
### Objetivo
Checar automaticamente se o aluno está elegível para acesso às dependências.
### Pré-condições
- Pagamento registrado ou atraso contabilizado.
### Pós-condições
- O status do aluno ("Regular", "Inadimplente") é gravado/atualizado.
### Fluxo Principal
1. Periodicamente, o sistema avalia as datas de vencimento de todos os alunos.
2. Para contas vencidas há mais de 5 dias, o status passa a "Inadimplente".
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF04
### RNF Relacionados
- RNF01, RNF03
### RN Relacionadas
- RN01, RN07

---

## UC08 — Liberar Acesso na Catraca
### Ator Principal
Sistema de Catraca (API)
### Objetivo
Validar via RFID se o aluno pode entrar na academia.
### Pré-condições
- O aluno passa o cartão/tag RFID na catraca.
### Pós-condições
- Catraca liberada e presença de acesso registrada, ou acesso negado.
### Fluxo Principal
1. A catraca envia o código RFID via API REST JSON ao sistema.
2. O sistema localiza o aluno e valida sua regularidade.
3. Se o limite de 5 dias de vencimento não foi excedido, retorna status "Autorizado".
4. A catraca é liberada fisicamente.
### Fluxos Alternativos
- **A1 — Aluno Inadimplente:** O sistema retorna status negado, exibindo bloqueio.
### RF Relacionados
- RF05
### RNF Relacionados
- RNF03, RNF06
### RN Relacionadas
- RN01

---

## UC09 — Visualizar Horários de Aulas
### Ator Principal
Aluno
### Objetivo
Permitir ao aluno checar a grade de aulas disponíveis.
### Pré-condições
- Estar logado no aplicativo.
### Pós-condições
- O aluno visualiza as aulas programadas, número de vagas e quem é o instrutor.
### Fluxo Principal
1. O aluno seleciona "Aulas Coletivas".
2. O sistema lista aulas, agrupadas por data e horário, com o status de vagas.
### Fluxos Alternativos
- N/A
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
Garantir uma vaga em aula específica.
### Pré-condições
- Aluno deve ser "Regular", e a turma deve ter vagas.
### Pós-condições
- O aluno ocupa uma vaga na aula desejada.
### Fluxo Principal
1. O aluno visualiza aula com vagas abertas e confirma reserva.
2. O sistema diminui as vagas disponíveis e salva a reserva do aluno.
3. O sistema envia a notificação de confirmação do agendamento.
### Fluxos Alternativos
- **A1 — Vagas Esgotadas:** O sistema bloqueia a nova reserva antes que a ação seja concluída.
### RF Relacionados
- RF06, RF10
### RNF Relacionados
- RNF04
### RN Relacionadas
- RN02

---

## UC11 — Cancelar Agendamento de Aula
### Ator Principal
Aluno
### Objetivo
Liberar a vaga previamente agendada caso o aluno não possa comparecer.
### Pré-condições
- O aluno ter um agendamento e estar a mais de 1 hora do início.
### Pós-condições
- Vaga é liberada no sistema.
### Fluxo Principal
1. O aluno seleciona a aula agendada.
2. Clica em Cancelar Reserva.
3. O sistema valida o tempo restante e cancela a reserva com sucesso.
### Fluxos Alternativos
- **A1 — Prazo Expirado:** O sistema recusa o cancelamento por ocorrer a menos de 1 hora do início.
### RF Relacionados
- RF06
### RNF Relacionados
- RNF04
### RN Relacionadas
- RN03

---

## UC12 — Registrar Presença em Aula
### Ator Principal
Instrutor
### Objetivo
Validar quais alunos da lista efetivamente compareceram à aula.
### Pré-condições
- O instrutor acessa o sistema pelo seu perfil na hora da aula.
### Pós-condições
- Percentual de faltas do aluno atualizado para relatórios.
### Fluxo Principal
1. Instrutor seleciona a aula agendada.
2. Sistema exibe a lista de alunos com reservas.
3. O instrutor marca "Presença" ou "Falta" para cada um e salva.
### Fluxos Alternativos
- N/A
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
Salvar laudos e medições para o histórico do aluno.
### Pré-condições
- Instrutor logado; aluno deve estar ativo e regular.
### Pós-condições
- Os dados (peso, IMC, dobras) e eventuais arquivos ficam salvos.
### Fluxo Principal
1. O instrutor pesquisa o aluno a ser avaliado.
2. O sistema valida o status de regularidade do aluno.
3. Instrutor insere os dados, anexa docs necessários e salva.
4. O sistema gera notificação de liberação da avaliação física ao aluno.
### Fluxos Alternativos
- **A1 — Aluno irregular:** O sistema bloqueia o registro exibindo as permissões RN05.
### RF Relacionados
- RF08, RF10
### RNF Relacionados
- RNF02, RNF04
### RN Relacionadas
- RN05, RN06

---

## UC14 — Visualizar Avaliação Física
### Ator Principal
Aluno
### Objetivo
Consultar a própria avaliação física registrada pelo instrutor.
### Pré-condições
- Avaliação foi liberada e estudante está logado.
### Pós-condições
- Aluno consegue visualizar seus dados e baixar anexos.
### Fluxo Principal
1. Aluno acessa o menu "Minhas Avaliações".
2. O sistema lista o histórico em ordem cronológica.
3. O aluno clica em uma delas e lê os detalhes (Peso, IMC).
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF08
### RNF Relacionados
- RNF02, RNF04
### RN Relacionadas
- N/A

---

## UC15 — Emitir Relatório de Inadimplência
### Ator Principal
Gerente
### Objetivo
Visualizar a quantidade e as informações dos alunos com mensalidade atrasada.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório em tela ou exportado.
### Fluxo Principal
1. Gerente acessa "Relatórios" > "Inadimplência".
2. Informa os filtros de unidade e datas.
3. O sistema calcula e exibe todos que caem na RN01.
### Fluxos Alternativos
- **A1 — Nenhum dado encontrado:** O sistema exibe um alerta de tabela vazia.
### RF Relacionados
- RF09
### RNF Relacionados
- RNF04, RNF05
### RN Relacionadas
- RN06

---

## UC16 — Emitir Relatório de Alunos Ativos
### Ator Principal
Gerente
### Objetivo
Levantar toda a base de matriculados que possuem pagamentos em dia.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório de alunos regulares exibido em tela.
### Fluxo Principal
1. Gerente acessa "Relatórios" > "Alunos Ativos".
2. Filtra por unidade/categoria de plano.
3. O sistema exibe a lista paginada de clientes regulares.
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF09
### RNF Relacionados
- RNF04, RNF05
### RN Relacionadas
- RN06

---

## UC17 — Emitir Relatório de Ocupação de Aulas
### Ator Principal
Gerente
### Objetivo
Analisar as aulas que mais atraem público e o nível de taxa de presença.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Métricas consolidadas por aula e professor.
### Fluxo Principal
1. Gerente acessa "Relatórios" > "Ocupação".
2. Insere um intervalo de tempo para análise.
3. O sistema cruza os limites de vagas vs. comparecimento (presenças do UC12) e exporta a estatística.
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF09
### RNF Relacionados
- RNF04, RNF05
### RN Relacionadas
- RN06

---

## UC18 — Enviar Notificação de Vencimento
### Ator Principal
Sistema
### Objetivo
Avisar o aluno da proximidade ou atraso da sua mensalidade por push/e-mail.
### Pré-condições
- A rotina de validação financeira deve estar rodando.
### Pós-condições
- Disparo do e-mail/push realizado.
### Fluxo Principal
1. O sistema filtra, de forma noturna/assíncrona, todos os alunos que vencerão em (X dias) ou atrasados.
2. O sistema compila a mensagem e envia.
3. Registra no log de "Notificações enviadas".
### Fluxos Alternativos
- **A1 — E-mail inválido:** O sistema arquiva a falha no log de e-mail devolvido.
### RF Relacionados
- RF10
### RNF Relacionados
- RNF01
### RN Relacionadas
- N/A

---

## UC19 — Atualizar Dados Cadastrais
### Ator Principal
Aluno / Recepcionista
### Objetivo
Configurar informações, atualizando mudança de endereço, telefone ou e-mail.
### Pré-condições
- Estar logado com o próprio usuário (Aluno) ou selecionando o aluno pela recepção.
### Pós-condições
- Informações modificadas e persistidas no banco.
### Fluxo Principal
1. O usuário acessa a rotina de "Meu Perfil" ou "Gerenciar Aluno".
2. Altera o dado necessário.
3. Clica em "Salvar Mudanças".
4. O sistema atualiza o registro.
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF01
### RNF Relacionados
- RNF02, RNF04
### RN Relacionadas
- RN06

---

## UC20 — Consultar Histórico de Acessos
### Ator Principal
Gerente
### Objetivo
Visualizar a tabela de logs de fluxo da catraca (entradas reais).
### Pré-condições
- Gerente autenticado no sistema.
### Pós-condições
- Leitura dos horários de pico e assiduidade física.
### Fluxo Principal
1. Gerente acessa a guia relatórios "Acessos de Catraca".
2. Filtra unidade, horários e dias da semana.
3. O sistema exibe o bloco de liberação gerado pelo UC08.
### Fluxos Alternativos
- N/A
### RF Relacionados
- RF09
### RNF Relacionados
- RNF05, RNF06
### RN Relacionadas
- RN06