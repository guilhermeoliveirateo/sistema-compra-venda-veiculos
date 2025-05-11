# Diagrama de Sequência

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

``` plantuml
@startuml

Title Diagrama de Sequência Unificado - Sistema de Compra e Venda de Veículos

actor Comprador
actor Vendedor
actor Admin
participant Sistema
participant Usuario
participant Anuncio
participant Veiculo
participant Pagamento
participant Negociacao
participant Mensagem
participant HistoricoTransacoes

Comprador -> Sistema : 1. criarPerfil()
activate Sistema
Sistema -> Usuario : 2. salvarUsuario
activate Usuario
Usuario --> Sistema : 3. confirmacaoPerfil
Sistema --> Comprador : 4. perfilCriado
deactivate Usuario
deactivate Sistema

Comprador -> Sistema : 5. fazerLogin(email, senha)
activate Sistema
Sistema -> Usuario : 6. verificarSenha(senha)
activate Usuario
Usuario --> Sistema : 7. senhaValida
Sistema --> Comprador : 8. loginRealizado
deactivate Usuario
deactivate Sistema

Comprador -> Sistema : 9. editarPerfil(...)
activate Sistema
Sistema -> Usuario : 10. editarDados
activate Usuario
Usuario --> Sistema : 11. dadosAtualizados
Sistema --> Comprador : 12. perfilAtualizado
deactivate Usuario
deactivate Sistema

Comprador -> Sistema : 13. excluirPerfil()
activate Sistema
Sistema -> Usuario : 14. excluirUsuario
activate Usuario
Usuario --> Sistema : 15. confirmaçãoExclusao
Sistema --> Comprador : 16. perfilExcluido
deactivate Usuario
deactivate Sistema

Vendedor -> Sistema : 17. criarAnuncio()
activate Sistema
Sistema -> Veiculo : 18. criarVeiculo(...)
activate Veiculo
Veiculo --> Sistema : 19. veiculoCriado
Sistema -> Anuncio : 20-23. adicionar info (descrição, preço, fotos, local)
activate Anuncio
Anuncio --> Sistema : 24. anuncioCriado
Sistema --> Vendedor : 25. anuncioPublicado
deactivate Veiculo
deactivate Anuncio
deactivate Sistema

Vendedor -> Sistema : 26. editarAnuncio()
activate Sistema
Sistema -> Anuncio : 27-30. alterar info
activate Anuncio
Anuncio --> Sistema : 31. anuncioAtualizado
Sistema --> Vendedor : 32. edicaoConcluida
deactivate Anuncio
deactivate Sistema

Vendedor -> Sistema : 33. removerAnuncio()
activate Sistema
Sistema -> Anuncio : 34. adicionarMotivoExclusao()
activate Anuncio
Anuncio --> Sistema : 35. statusRemovido
Sistema --> Vendedor : 36. anuncioRemovido
deactivate Anuncio
deactivate Sistema

Comprador -> Sistema : 37. buscarVeiculo()
activate Sistema
Sistema -> Anuncio : 38. filtrarDescricaoPreco()
activate Anuncio
Anuncio --> Sistema : 39. listaAnuncios
Sistema --> Comprador : 40. resultadosEncontrados
deactivate Anuncio
deactivate Sistema

Comprador -> Sistema : 41. visualizarDetalhes()
activate Sistema
Sistema -> Anuncio : 42. detalhesAnuncio
activate Anuncio
Anuncio --> Sistema : 43. dadosAnuncio
Sistema --> Comprador : 44. exibeDetalhes
deactivate Anuncio
deactivate Sistema

Comprador -> Sistema : 45. acompanharStatus()
activate Sistema
Sistema -> Anuncio : 46. statusAnuncio
activate Anuncio
Anuncio --> Sistema : 47. statusAtual
Sistema --> Comprador : 48. statusExibido
deactivate Anuncio
deactivate Sistema

Comprador -> Sistema : 49. iniciarNegociacao(vendedor, anuncio)
activate Sistema
Sistema -> Negociacao : 50. criarNegociacao()
activate Negociacao
Negociacao --> Sistema : 51. negociação criada
Sistema --> Comprador : 52. negociação iniciada
deactivate Negociacao
deactivate Sistema

Comprador -> Sistema : 53. enviarMensagem(texto)
activate Sistema
Sistema -> Mensagem : 54. salvarMensagem()
activate Mensagem
Mensagem --> Sistema : 55. mensagemRegistrada
Sistema --> Comprador : 56. mensagemEnviada
deactivate Mensagem
deactivate Sistema

Vendedor -> Sistema : 57. responderMensagem()
activate Sistema
Sistema -> Mensagem : 58. salvarResposta()
activate Mensagem
Mensagem --> Sistema : 59. resposta salva
Sistema --> Vendedor : 60. resposta enviada
deactivate Mensagem
deactivate Sistema

Comprador -> Sistema : 61. confirmarPagamento()
activate Sistema
Sistema -> Pagamento : 62. registrarPagamento
activate Pagamento
Pagamento --> Sistema : 63. statusPago
Sistema --> Comprador : 64. pagamentoConfirmado
deactivate Pagamento
deactivate Sistema

Vendedor -> Sistema : 65. definirComoVendido(veiculo)
activate Sistema
Sistema -> Pagamento : 66. verificarPagamento()
activate Pagamento
Pagamento --> Sistema : 67. pagamento confirmado

Sistema -> Sistema : 68. notificarConfirmacao()
Sistema --> Vendedor : 69. confirmação enviada

Sistema -> Veiculo : 70. alterarStatus(vendido)
activate Veiculo
Veiculo --> Sistema : 71. status alterado
Sistema --> Vendedor : 72. veículo marcado como vendido
deactivate Pagamento
deactivate Veiculo
deactivate Sistema

Comprador -> Sistema : 73. consultarHistoricoCompras()
activate Sistema
Sistema -> HistoricoTransacoes : 74. buscarCompras
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 75. listaTransacoes
Sistema --> Comprador : 76. histórico de compras
deactivate HistoricoTransacoes
deactivate Sistema

Vendedor -> Sistema : 77. consultarHistoricoVendas()
activate Sistema
Sistema -> HistoricoTransacoes : 78. buscarVendas
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 79. listaTransacoes
Sistema --> Vendedor : 80. histórico de vendas
deactivate HistoricoTransacoes
deactivate Sistema

Sistema -> Sistema : 81. visualizarDetalhesVenda(id)
Sistema --> Vendedor : 82. detalhes da venda

Sistema -> Sistema : 83. visualizarDetalhesCompra(id)
Sistema --> Comprador : 84. detalhes da compra

Admin -> Sistema : 85. gerenciarUsuarios()
activate Usuario
Sistema -> Usuario : 86. listar/editar/excluir
Usuario --> Sistema : 87. operação concluída
Sistema --> Admin : 88. gestão de usuários concluída
deactivate Usuario

Admin -> Sistema : 89. gerenciarAnuncios()
activate Anuncio
Sistema -> Anuncio : 90. listar/editar/remover
Anuncio --> Sistema : 91. operação concluída
Sistema --> Admin : 92. gestão de anúncios concluída
deactivate Anuncio

deactivate Sistema

@enduml
```

