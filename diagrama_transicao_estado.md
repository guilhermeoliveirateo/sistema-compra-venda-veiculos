# Diagrama de Transição de Estado — Sistema de Compra e Venda de Veículos

```plantuml
' ================== Diagrama de Estado: Anúncio ==================
state "Anúncio" as Anuncio {
  [*] --> Criado : Criar anúncio
  Criado --> Ativo : Publicar anúncio
  Ativo --> EmNegociacao : Iniciar negociação
  EmNegociacao --> Vendido : Confirmar pagamento\nDefinir como vendido
  EmNegociacao --> Ativo : Cancelar negociação
  Ativo --> Editado : Editar anúncio
  Editado --> Ativo : Publicar alterações
  Ativo --> Removido : Remover anúncio\nAdicionar motivo
  Vendido --> Arquivado : Concluir venda
  Removido --> [*]
  Arquivado --> [*]
}

' ================== Diagrama de Estado: Veículo ==================
state "Veículo" as Veiculo {
  [*] --> Criado : Criar veículo
  Criado --> Disponível : Associar a um anúncio
  Disponível --> EmNegociacao : Iniciar negociação
  EmNegociacao --> Vendido : Confirmar venda
  Vendido --> Arquivado : Encerrar venda
  Disponível --> Editado : Editar veículo
  Editado --> Disponível : Salvar alterações
  Disponível --> Removido : Remover veículo
  Removido --> [*]
  Arquivado --> [*]
}

' ================== Diagrama de Estado: Usuário ==================
state "Usuário" as Usuario {
  [*] --> Registrado : Criar perfil
  Registrado --> Ativo : Verificar email / Login válido
  Ativo --> Editado : Editar perfil
  Editado --> Ativo : Salvar alterações
  Ativo --> Inativo : Inatividade\nViolação de regras
  Ativo --> Excluido : Excluir conta
  Excluido --> [*]
  Inativo --> Ativo : Reativar conta
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