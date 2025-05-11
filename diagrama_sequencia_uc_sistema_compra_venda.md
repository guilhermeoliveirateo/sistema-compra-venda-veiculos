# Diagrama de Sequência

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

```plantuml
@startuml

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

Comprador -> Sistema : 1. iniciarNegociacao(vendedor, anuncio)
activate Sistema
Sistema -> Negociacao : 2. criarNegociacao()
activate Negociacao
Negociacao --> Sistema : 3. negociacaoCriada
Sistema --> Comprador : 4. negociacaoIniciada

Comprador -> Sistema : 5. enviarMensagem()
activate Mensagem
Sistema -> Mensagem : 6. salvarMensagem()
Mensagem --> Sistema : 7. confirmacaoMensagem
Sistema --> Comprador : 8. mensagemEnviada

Vendedor -> Sistema : 9. responderMensagem()
Sistema -> Mensagem : 10. salvarResposta()
Mensagem --> Sistema : 11. respostaSalva
Sistema --> Vendedor : 12. respostaEnviada

Vendedor -> Sistema : 13. definirComoVendido()
activate Sistema
Sistema -> Pagamento : 14. verificarPagamento()
activate Pagamento
Pagamento --> Sistema : 15. pagamentoConfirmado

Sistema -> Sistema : 16. notificarConfirmacao()
activate Sistema
Sistema --> Vendedor : 17. confirmacaoEnviada

Sistema -> Veiculo : 18. alterarStatus()
activate Veiculo
Veiculo --> Sistema : 19. statusAlterado
Sistema --> Vendedor : 20. veiculoMarcadoVendido

Vendedor -> Sistema : 21. consultarHistoricoVendas()
activate HistoricoTransacoes
Sistema -> HistoricoTransacoes : 22. buscarTransacoes()
HistoricoTransacoes --> Sistema : 23. transacoesEncontradas
Sistema --> Vendedor : 24. historicoVendas

Sistema -> Sistema : 25. visualizarDetalhesVenda()
activate Sistema
Sistema --> Vendedor : 26. detalhesVenda

Comprador -> Sistema : 27. consultarHistoricoCompras()
Sistema -> HistoricoTransacoes : 28. buscarTransacoes()
HistoricoTransacoes --> Sistema : 29. transacoesEncontradas
Sistema --> Comprador : 30. historicoCompras

Sistema -> Sistema : 31. visualizarDetalhesCompra()
activate Sistema
Sistema --> Comprador : 32. detalhesCompra

Admin -> Sistema : 33. gerenciarUsuarios()
activate Usuario
Sistema -> Usuario : 34. listar/editar/excluir
Usuario --> Sistema : 35. operacaoConcluida
Sistema --> Admin : 36. gestaoUsuariosConcluida

Admin -> Sistema : 37. gerenciarAnuncios()
activate Anuncio
Sistema -> Anuncio : 38. listar/editar/remover
Anuncio --> Sistema : 39. operacaoConcluida
Sistema --> Admin : 40. gestaoAnunciosConcluida

deactivate Sistema
@enduml
```