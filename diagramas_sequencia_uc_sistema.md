# Diagrama de Sequência de Mensagens

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

```plantuml
@startuml

actor Comprador
actor Vendedor
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
deactivate Usuario
Sistema --> Comprador : 4. perfilCriado
deactivate Sistema

Comprador -> Sistema : 5. fazerLogin(email, senha)
activate Sistema
Sistema -> Usuario : 6. verificarSenha()
activate Usuario
Usuario --> Sistema : 7. senhaValida
deactivate Usuario
Sistema --> Comprador : 8. loginRealizado
deactivate Sistema

Comprador -> Sistema : 9. editarPerfil()
activate Sistema
Sistema -> Usuario : 10. editarDados
activate Usuario
Usuario --> Sistema : 11. dadosAtualizados
deactivate Usuario
Sistema --> Comprador : 12. perfilAtualizado
deactivate Sistema

Comprador -> Sistema : 13. excluirPerfil()
activate Sistema
Sistema -> Usuario : 14. excluirUsuario
activate Usuario
Usuario --> Sistema : 15. confirmaçãoExclusao
deactivate Usuario
Sistema --> Comprador : 16. perfilExcluido
deactivate Sistema

Vendedor -> Sistema : 17. criarAnuncio()
activate Sistema
Sistema -> Veiculo : 18. adicionarVeiculo()
activate Veiculo
Veiculo --> Sistema : 19. veiculoCriado
deactivate Veiculo
Sistema -> Anuncio : 20. adicionarDescricao()
Sistema -> Anuncio : 21. adicionarPreco()
Sistema -> Anuncio : 22. adicionarFotos()
Sistema -> Anuncio : 23. adicionarLocalizacao()
activate Anuncio
Anuncio --> Sistema : 24. anuncioCriado
deactivate Anuncio
Sistema --> Vendedor : 25. anuncioPublicado
deactivate Sistema

Vendedor -> Sistema : 26. editarAnuncio()
activate Sistema
Sistema -> Anuncio : 27. alterarDescricao()
Sistema -> Anuncio : 28. alterarPreco()
Sistema -> Anuncio : 29. alterarFotos()
Sistema -> Anuncio : 30. alterarLocalizacao()
activate Anuncio
Anuncio --> Sistema : 31. anuncioAtualizado
deactivate Anuncio
Sistema --> Vendedor : 32. edicaoConcluida
deactivate Sistema

Vendedor -> Sistema : 33. removerAnuncio()
activate Sistema
Sistema -> Anuncio : 34. adicionarMotivoExclusao
activate Anuncio
Anuncio --> Sistema : 35. statusRemovido
deactivate Anuncio
Sistema --> Vendedor : 36. anuncioRemovido
deactivate Sistema

Comprador -> Sistema : 37. buscarVeiculo()
activate Sistema
Sistema -> Anuncio : 38. filtrarDescricaoPreco
activate Anuncio
Anuncio --> Sistema : 39. listaAnuncios
deactivate Anuncio
Sistema --> Comprador : 40. resultadosEncontrados
deactivate Sistema

Comprador -> Sistema : 41. visualizarDetalhes(anuncio)
activate Sistema
Sistema -> Anuncio : 42. detalhesAnuncio
activate Anuncio
Anuncio --> Sistema : 43. dadosAnuncio
deactivate Anuncio
Sistema --> Comprador : 44. exibeDetalhes
deactivate Sistema

Comprador -> Sistema : 45. acompanharStatus(anuncio)
activate Sistema
Sistema -> Anuncio : 46. statusAnuncio
activate Anuncio
Anuncio --> Sistema : 47. statusAtual
deactivate Anuncio
Sistema --> Comprador : 48. statusExibido
deactivate Sistema

Comprador -> Sistema : 49. iniciarNegociacao(vendedor, anuncio)
activate Sistema
Sistema -> Negociacao : 50. iniciarNegociacao
activate Negociacao
Negociacao --> Sistema : 51. statusEmAndamento
deactivate Negociacao
Sistema --> Comprador : 52. negociacaoIniciada
deactivate Sistema

Comprador -> Sistema : 53. enviarMensagem()
activate Sistema
Sistema -> Mensagem : 54. enviarVendedor
activate Mensagem
Mensagem --> Sistema : 55. mensagemRegistrada
deactivate Mensagem
Sistema --> Comprador : 56. mensagemEnviada
deactivate Sistema

Comprador -> Sistema : 57. confirmarPagamento()
activate Sistema
Sistema -> Pagamento : 58. registrarPagamento
activate Pagamento
Pagamento --> Sistema : 59. statusPago
deactivate Pagamento
Sistema --> Comprador : 60. pagamentoConfirmado
deactivate Sistema

Comprador -> Sistema : 61. consultarHistoricoCompras()
activate Sistema
Sistema -> HistoricoTransacoes : 62. buscarCompras
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 63. listaTransacoes
deactivate HistoricoTransacoes
Sistema --> Comprador : 64. historicoExibido
deactivate Sistema

Vendedor -> Sistema : 65. consultarHistoricoVendas()
activate Sistema
Sistema -> HistoricoTransacoes : 66. buscarVendas
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 67. listaVendas
deactivate HistoricoTransacoes
Sistema --> Vendedor : 68. historicoExibido
deactivate Sistema

@enduml
```