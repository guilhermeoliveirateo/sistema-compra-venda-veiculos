```@startuml
title Diagrama de Transição de Estado - Sistema Completo

[*] --> Criando perfil

Criando perfil --> Fazendo login : Após criação
Fazendo login --> Editando perfil : Ação do usuário
Editando perfil --> Visualizando perfil
Visualizando perfil --> Fazendo login

Fazendo login --> Buscando veículos
Fazendo login --> Criando anúncio
Fazendo login --> Excluindo perfil : Solicitação do usuário
Excluindo perfil --> [*]

Buscando veículos --> Visualizando detalhes
Visualizando detalhes --> Iniciando negociação

Iniciando negociação --> Enviando mensagem
Enviando mensagem --> Respondendo mensagem
Respondendo mensagem --> Finalizando negociação
Finalizando negociação --> Confirmando pagamento
Confirmando pagamento --> Verificando pagamento
Verificando pagamento --> Notificando confirmação
Notificando confirmação --> Marcando como vendido
Marcando como vendido --> Consultando histórico de compras
Marcando como vendido --> Consultando histórico de vendas
Consultando histórico de compras --> [*]
Consultando histórico de vendas --> [*]

Criando anúncio --> Anuncio

state "Anúncio" as Anuncio {
  [*] --> Criando rascunho : Início
  Criando rascunho --> Publicando : Criar e salvar
  Publicando --> Anúncio publicado
  Anúncio publicado --> Iniciando negociação : Interesse recebido
  Iniciando negociação --> Marcando como vendido : Venda concluída
  Marcando como vendido --> Arquivando : Finalização
  Arquivando --> [*]

  Anúncio publicado --> Editando anúncio : Edição manual
  Editando anúncio --> Anúncio publicado : Salvar edição
  Anúncio publicado --> Removendo : Exclusão manual
  Removendo --> [*]
}

Criando anúncio --> Associando veículo

state "Veículo" as Veiculo {
  [*] --> Registrando : Cadastro
  Registrando --> Associando : Associar ao anúncio
  Associando --> Em negociação : Proposta recebida
  Em negociação --> Vendido : Confirmada
  Vendido --> Arquivando veículo : Finalizado
  Arquivando veículo --> [*]

  Registrando --> Inativando : Nunca anunciado
  Inativando --> [*]
  Associando --> Inativando : Anúncio removido
}

state "Usuário" as Usuario {
  [*] --> Registrando usuário : Cadastro
  Registrando usuário --> Ativando conta : Login confirmado
  Ativando conta --> Editando perfil
  Editando perfil --> Ativando conta : Salvar
  Ativando conta --> Inativando conta : Pausar
  Inativando conta --> Ativando conta : Reativar
  Ativando conta --> Excluindo perfil : Deletar conta
  Excluindo perfil --> [*]
}

state "Pagamento" as Pagamento {
  [*] --> Iniciando pagamento : Negociação finalizada
  Iniciando pagamento --> Processando pagamento
  Processando pagamento --> Confirmando pagamento
  Confirmando pagamento --> Concluindo pagamento : Repasse feito
  Concluindo pagamento --> [*]

  Iniciando pagamento --> Cancelando pagamento : Falha ou desistência
  Cancelando pagamento --> [*]
}

state "Negociação" as Negociacao {
  [*] --> Iniciando : Contato aberto
  Iniciando --> Em andamento : Mensagens trocadas
  Em andamento --> Aceitando proposta
  Aceitando proposta --> Finalizando negociação : Confirmação
  Finalizando negociação --> [*]

  Em andamento --> Cancelando negociação : Desistência
  Cancelando negociação --> [*]
}

@enduml
```