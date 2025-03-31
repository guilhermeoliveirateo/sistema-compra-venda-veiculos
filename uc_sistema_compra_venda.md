# Diagrama de Casos de Uso

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

```plantuml
@startuml

left to right direction
actor "Comprador" as comprador
actor "Vendedor" as vendedor

rectangle "Sistema de compra e venda de veículos"{
  usecase "Negociar condições de venda" as uc1
  usecase "Enviar mensagens" as uc2
  usecase "Definir veículo como vendido" as uc3
  usecase "Consultar histórico de vendas" as uc4
  usecase "Consultar histórico de compras" as uc5
  usecase "Verificar pagamento" as uc6
  usecase "Notificar confirmação" as uc7
  usecase "Alterar status do veículo" as uc8
  usecase "Visualizar detalhes por venda" as uc9
  usecase "Gerenciar usuários" as uc10
  usecase "Gerenciar anúncios" as uc11
  usecase "Visualizar detalhes por compra" as uc12
}

actor "API de pagamento" as pagamento
actor "Sistema" as sistema
actor "Admin" as admin

vendedor -- uc1
comprador -- uc1
uc1 ..> uc2 :<<include>>
vendedor -- uc3
uc3 ..> uc6 :<<include>>
uc3 ..> uc7 :<<include>>
uc3 ..> uc8 :<<include>>
uc6 -- pagamento
uc7 -- sistema
uc8 -- sistema
vendedor -- uc4
uc4 <.. uc9 :<<extends>>
comprador -- uc5
uc5 <.. uc12 :<<extends>>
admin -- uc10
admin -- uc11

sistema -[hidden]-> admin
pagamento -[hidden]-> admin

@enduml
```
