# Diagrama de Transição de Estado — Sistema de Compra e Venda de Veículos

```plantuml
' ============================
' Diagrama de estado do ANÚNCIO
' ============================
state "Anúncio" as Anuncio {
  [*] --> Rascunho : Criar
  Rascunho --> Publicado : Publicar
  Publicado --> EmNegociacao : Negociação iniciada
  EmNegociacao --> Vendido : Confirmação de pagamento
  Vendido --> Arquivado : Finalização
  Publicado --> Editado : Editar conteúdo
  Editado --> Publicado : Salvar edição
  Publicado --> Removido : Remoção manual
}

' ============================
' Diagrama de estado do VEÍCULO
' ============================
state "Veículo" as Veiculo {
  [*] --> Registrado : Cadastrado no sistema
  Registrado --> Anunciado : Associado a anúncio
  Anunciado --> EmNegociacao : Negociação ativa
  EmNegociacao --> Vendido : Confirmação da venda
  Vendido --> Arquivado : Concluído
  Registrado --> Inativo : Nunca anunciado
  Anunciado --> Inativo : Anúncio removido
}

' ============================
' Diagrama de estado do USUÁRIO
' ============================
state "Usuário" as Usuario {
  [*] --> Registrado : Cadastro
  Registrado --> Ativo : Login confirmado
  Ativo --> Editando : Alteração de perfil
  Editando --> Ativo : Confirmação de edição
  Ativo --> Inativo : Pausar conta
  Inativo --> Ativo : Reativar
  Ativo --> Excluido : Deletar conta
}

' ================== Diagrama de Estado: Pagamento ==================
state "Pagamento" as Pagamento {
  [*] --> Pendente : Iniciar negociação
  Pendente --> EmProcessamento : Efetuar pagamento
  EmProcessamento --> Confirmado : API confirma
  EmProcessamento --> Falhou : Erro no pagamento
  Confirmado --> Notificado : Enviar confirmação
  Notificado --> [*]
  Falhou --> [*]
}

' ================== Diagrama de Estado: Negociação ==================
state "Negociação" as Negociacao {
  [*] --> Iniciada : Comprador inicia
  Iniciada --> EmAndamento : Troca de mensagens
  EmAndamento --> Concluida : Confirmação da venda
  EmAndamento --> Cancelada : Cancelamento
  Concluida --> [*]
  Cancelada --> [*]
}
@enduml
```