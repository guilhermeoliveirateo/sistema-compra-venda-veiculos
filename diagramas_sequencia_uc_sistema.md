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

Vendedor -> Sistema : 27. removerAnuncio()
activate Sistema
Sistema -> Anuncio : 28. adicionarMotivoExclusao
activate Anuncio
Anuncio --> Sistema : 29. statusRemovido
deactivate Anuncio
Sistema --> Vendedor : 30. anuncioRemovido
deactivate Sistema

Comprador -> Sistema : 31. buscarVeiculo()
activate Sistema
Sistema -> Anuncio : 32. filtrar por descrição/preço
activate Anuncio
Anuncio --> Sistema : 33. lista de anúncios
deactivate Anuncio
Sistema --> Comprador : 34. resultados encontrados
deactivate Sistema

Comprador -> Sistema : 35. visualizarDetalhes(anuncio)
activate Sistema
Sistema -> Anuncio : 36. detalhes do anúncio
activate Anuncio
Anuncio --> Sistema : 37. dados do anúncio
deactivate Anuncio
Sistema --> Comprador : 38. exibe detalhes
deactivate Sistema

Comprador -> Sistema : 39. acompanharStatus(anuncio)
activate Sistema
Sistema -> Anuncio : 40. status do anúncio
activate Anuncio
Anuncio --> Sistema : 41. status atual
deactivate Anuncio
Sistema --> Comprador : 42. status exibido
deactivate Sistema

Comprador -> Sistema : 43. iniciarNegociacao(vendedor, anuncio)
activate Sistema
Sistema -> Negociacao : 44. iniciar negociação
activate Negociacao
Negociacao --> Sistema : 45. status = em andamento
deactivate Negociacao
Sistema --> Comprador : 46. negociação iniciada
deactivate Sistema

Comprador -> Sistema : 47. enviarMensagem()
activate Sistema
Sistema -> Mensagem : 48. enviar para vendedor
activate Mensagem
Mensagem --> Sistema : 49. mensagem registrada
deactivate Mensagem
Sistema --> Comprador : 50. mensagem enviada
deactivate Sistema

Comprador -> Sistema : 51. confirmarPagamento()
activate Sistema
Sistema -> Pagamento : 52. registrar pagamento
activate Pagamento
Pagamento --> Sistema : 53. status = pago
deactivate Pagamento
Sistema --> Comprador : 54. pagamento confirmado
deactivate Sistema

Comprador -> Sistema : 55. consultarHistoricoCompras()
activate Sistema
Sistema -> HistoricoTransacoes : 56. buscar compras
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 57. lista de transações
deactivate HistoricoTransacoes
Sistema --> Comprador : 58. histórico exibido
deactivate Sistema

Vendedor -> Sistema : 59. consultarHistoricoVendas()
activate Sistema
Sistema -> HistoricoTransacoes : 60. buscar vendas
activate HistoricoTransacoes
HistoricoTransacoes --> Sistema : 61. lista de vendas
deactivate HistoricoTransacoes
Sistema --> Vendedor : 62. histórico exibido
deactivate Sistema

@enduml
```