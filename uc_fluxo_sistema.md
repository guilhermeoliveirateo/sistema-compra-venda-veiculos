# Diagrama de Casos de Uso

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

``` plantuml
@startuml 

left to right direction
actor "Comprador" as comprador
actor "Vendedor" as vendedor

rectangle "Sistema de venda e compra de veículos"{
usecase "Fazer login" as uc1
usecase "Editar perfil" as uc2
usecase "Criar anúncio" as uc3
usecase "Editar anúncio" as uc4
usecase "Remover anúncio" as uc5
usecase "Buscar veículo" as uc6
usecase "Verificar senha" as uc7
usecase "Exibir mensagem de erro" as uc8
usecase "Adicionar descrição" as uc9
usecase "Definir preço do veículo" as uc10
usecase "Alterar descrição" as uc11
usecase "Alterar preço" as uc12
usecase "Adicionar motivo da exclusão" as uc13
usecase "Visualizar detalhes" as uc14
usecase "Acompanhar status" as uc15
usecase "Criar perfil" as uc16
usecase "Adicionar fotos" as uc17
usecase "Adicionar localização" as uc18
usecase "Alterar fotos" as uc19
usecase "Alterar localização" as uc20
}

vendedor -- uc16
comprador -- uc16
vendedor -- uc1
comprador -- uc1
uc1 ..> uc7 :<<include>>
uc1 <.. uc8 :<<extends>>
vendedor -- uc2
comprador -- uc2
vendedor -- uc3
uc3 ..> uc9 :<<include>>
uc3 ..> uc10 :<<include>>
uc3 ..> uc17 :<<include>>
uc3 ..> uc18 :<<include>>
vendedor -- uc4
uc4 ..> uc11 :<<include>>
uc4 ..> uc12 :<<include>>
uc4 ..> uc19 :<<include>>
uc4 ..> uc20 :<<include>>
vendedor -- uc5
uc5 ..> uc13 :<<include>>
comprador -- uc6
uc6 <.. uc14 :<<extends>>
uc14 <.. uc15 :<<extends>>
 
@enduml
```