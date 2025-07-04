# Diagrama de Casos de Uso

``` plantuml
@startuml 

left to right direction
actor "Comprador" as comprador
actor "Vendedor" as vendedor

rectangle "Sistema de compra e venda de veículos"{
usecase "Fazer login" as uc1
usecase "Editar perfil" as uc2
usecase "Criar anúncio" as uc3
usecase "Editar anúncio" as uc4
usecase "Remover anúncio" as uc5
usecase "Buscar veículo" as uc6
usecase "Verificar senha" as uc7
usecase "Exibir mensagem de erro" as uc8
usecase "Adicionar descrição" as uc9
usecase "Adicionar preço do veículo" as uc10
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
usecase "Excluir perfil" as uc21
}

actor "Sistema" as sistema

vendedor -- uc16
comprador -- uc16
vendedor -- uc1
comprador -- uc1
uc1 ..> uc7 :<<include>>
uc7 <.. uc8 :<<extends>>
uc1 <.. uc2 :<<include>>
uc1 <.. uc3 :<<include>>
uc1 <.. uc4 :<<include>>
uc1 <.. uc5 :<<include>>
uc1 <.. uc6 :<<include>>
uc1 <.. uc21 :<<include>>
vendedor -- uc2
comprador -- uc2
vendedor -- uc21
comprador -- uc21
vendedor -- uc3
uc3 ..> uc9 :<<include>>
uc3 ..> uc10 :<<include>>
uc3 ..> uc17 :<<include>>
uc3 ..> uc18 :<<include>>
vendedor -- uc4
uc4 ..> uc11 :<<extends>>
uc4 ..> uc12 :<<extends>>
uc4 ..> uc19 :<<extends>>
uc4 ..> uc20 :<<extends>>
vendedor -- uc5
uc5 ..> uc13 :<<include>>
comprador -- uc6
uc6 <.. uc14 :<<extends>>
uc14 <.. uc15 :<<extends>>
uc4 ..> uc3 :<<include>>
uc5 ..> uc3 :<<include>>
uc7 -- sistema
uc8 -- sistema
uc2 ..> uc16 <<include>>
uc21 ..> uc16 <<include>>
 
@enduml
```
