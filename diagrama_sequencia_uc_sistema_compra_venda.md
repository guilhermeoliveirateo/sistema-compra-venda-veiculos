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

Vendedor -> Sistema : 13. definirComoVendido(veiculo)
activate Sistema
Sistema -> Pagamento : 14. verificarPagamento()
activate Pagamento
Pagamento --> Sistema : 15. pagamento confirmado

Sistema -> Sistema : 16. notificarConfirmacao()
activate Sistema
Sistema --> Vendedor : 17. confirmação enviada

Sistema -> Veiculo : 18. alterarStatus(vendido)
activate Veiculo
Veiculo --> Sistema : 19. status alterado
Sistema --> Vendedor : 20. veículo marcado como vendido

Vendedor -> Sistema : 21. consultarHistoricoVendas()
activate HistoricoTransacoes
Sistema -> HistoricoTransacoes : 22. buscarTransacoes(tipo=venda)
HistoricoTransacoes --> Sistema : 23. transações encontradas
Sistema --> Vendedor : 24. histórico de vendas

Sistema -> Sistema : 25. visualizarDetalhesVenda(id)
activate Sistema
Sistema --> Vendedor : 26. detalhes da venda

Comprador -> Sistema : 27. consultarHistoricoCompras()
Sistema -> HistoricoTransacoes : 28. buscarTransacoes(tipo=compra)
HistoricoTransacoes --> Sistema : 29. transações encontradas
Sistema --> Comprador : 30. histórico de compras

Sistema -> Sistema : 31. visualizarDetalhesCompra(id)
activate Sistema
Sistema --> Comprador : 32. detalhes da compra

Admin -> Sistema : 33. gerenciarUsuarios()
activate Usuario
Sistema -> Usuario : 34. listar/editar/excluir
Usuario --> Sistema : 35. operação concluída
Sistema --> Admin : 36. gestão concluo conclu\uída

Admin -> Sistema : 37. gerenciarAnuncios()
activate Anuncio
Sistema -> Anuncio : 38. listar/editar/remover
Anuncio --> Sistema : 39. operação concluída
Sistema --> Admin : 40. gestão de anúncio concluída

deactivate Sistema
@enduml
```