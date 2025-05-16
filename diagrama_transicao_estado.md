# Diagrama de Transição de Estado

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

```plantuml
@startuml

state "Anúncio" as Anuncio {
  [*] --> Criando : Criar
  Criando --> Publicando : Publicar
  Publicando --> Negociando : Negociação iniciada
  Negociando --> Vendendo : Confirmação de pagamento
  Vendendo --> Arquivando : Finalizado
  Arquivando --> [*] : Encerrar anúncio

  Publicando --> Editando : Editar conteúdo
  Editando --> Publicando : Salvar edição
  Publicando --> Removendo : Remoção manual
  Removendo --> [*] : Anúncio removido
}

state "Veículo" as Veiculo {
  [*] --> Registrando : Cadastrado no sistema
  Registrando --> Anunciando : Associado a anúncio
  Anunciando --> Negociando : Negociação ativa
  Negociando --> Vendendo : Confirmação da venda
  Vendendo --> Arquivando : Concluído
  Arquivando --> [*] : Arquivar veículo

  Registrando --> Inativando : Nunca anunciado
  Inativando --> [*] : Encerrado sem anúncio
  Anunciando --> Inativando : Anúncio removido
}

state "Usuário" as Usuario {
  [*] --> Registrando : Cadastro
  Registrando --> Ativando : Login confirmado
  Ativando --> Editando : Alteração de perfil
  Editando --> Ativando : Confirmação de edição
  Ativando --> Inativando : Pausar conta
  Inativando --> Ativando : Reativar
  Ativando --> Excluindo : Deletar conta
  Excluindo --> [*] : Conta excluída
}

state "Pagamento" as Pagamento {
  [*] --> Iniciando : Início do processo
  Iniciando --> Processando : Processando dados
  Processando --> Confirmando : Confirmação pelo sistema
  Confirmando --> Concluindo : Repasse efetuado
  Concluindo --> [*] : Pagamento concluído

  Iniciando --> Cancelando : Erro ou desistência
  Cancelando --> [*] : Pagamento cancelado
}

state "Negociação" as Negociacao {
  [*] --> Iniciando : Contato inicial
  Iniciando --> Desenvolvendo : Envio de mensagens
  Desenvolvendo --> Aceitando : Termos definidos
  Aceitando --> Finalizando : Venda confirmada
  Finalizando --> [*] : Negociação finalizada

  Desenvolvendo --> Cancelando : Desistência
  Cancelando --> [*] : Negociação cancelada
}

@enduml
```