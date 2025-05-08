# Diagramas de Sequência - Sistema de Compra e Venda de Veículos

## Fazer login

```plantuml
@startuml
actor Usuario
participant "Sistema" as Sistema
participant "UsuarioService" as Service
participant "Usuario" as Usuario

Usuario -> Sistema : fazerLogin(email, senha)
Sistema -> Service : verificarCredenciais(email, senha)
Service -> Usuario : verificarSenha(senha)
Usuario --> Service : true/false
Service --> Sistema : resultadoLogin
Sistema --> Usuario : acessoPermitido/negado
@enduml
```

## Editar perfil

```plantuml
@startuml
actor Usuario
participant "Sistema" as Sistema
participant "UsuarioService" as Service
participant "Usuario" as UsuarioClass

Usuario -> Sistema : editarPerfil(novosDados)
Sistema -> Service : atualizarPerfil(novosDados)
Service -> UsuarioClass : setDados(novosDados)
UsuarioClass --> Service : atualizado
Service --> Sistema : sucesso
Sistema --> Usuario : perfilAtualizado
@enduml
```

## Criar anúncio

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Veiculo" as Veiculo
participant "Anuncio" as Anuncio

Vendedor -> Sistema : criarAnuncio(dadosVeiculo, descricao, preco)
Sistema -> Service : criarAnuncio(dadosVeiculo, descricao, preco)
Service -> Veiculo : criar(dadosVeiculo)
Veiculo --> Service : novoVeiculo
Service -> Anuncio : instanciar(novoVeiculo, descricao, preco)
Anuncio --> Service : novoAnuncio
Service --> Sistema : anuncioCriado
Sistema --> Vendedor : confirmacao
@enduml
```

## Editar anúncio

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : editarAnuncio(idAnuncio, novosDados)
Sistema -> Service : editarAnuncio(idAnuncio, novosDados)
Service -> Anuncio : atualizar(novosDados)
Anuncio --> Service : atualizado
Service --> Sistema : sucesso
Sistema --> Vendedor : anuncioAtualizado
@enduml
```

## Remover anúncio

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : removerAnuncio(idAnuncio, motivo)
Sistema -> Service : removerAnuncio(idAnuncio, motivo)
Service -> Anuncio : registrarMotivo(motivo)
Anuncio --> Service : ok
Service -> Anuncio : marcarComoRemovido()
Anuncio --> Service : confirmado
Service --> Sistema : anuncio removido
Sistema --> Vendedor : confirmação
@enduml
```

## Buscar veículo

```plantuml
@startuml
actor Comprador
participant "Sistema" as Sistema
participant "AnuncioService" as Service

Comprador -> Sistema : buscarVeiculo(filtros)
Sistema -> Service : buscarAnuncios(filtros)
Service --> Sistema : listaAnuncios
Sistema --> Comprador : exibirResultados
@enduml
```

## Verificar senha

```plantuml
@startuml
actor Sistema
participant "Usuario" as Usuario

Sistema -> Usuario : verificarSenha(senha)
Usuario --> Sistema : true/false
@enduml
```

## Exibir mensagem de erro

```plantuml
@startuml
actor Sistema
participant "Interface" as UI

Sistema -> UI : mostrarMensagem("Erro de autenticação")
@enduml
```

## Adicionar descrição

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "Anuncio" as Anuncio

Vendedor -> Sistema : adicionarDescricao(idAnuncio, descricao)
Sistema -> Anuncio : setDescricao(descricao)
Anuncio --> Sistema : confirmado
Sistema --> Vendedor : descrição adicionada
@enduml
```

## Adicionar preço do veículo

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "Anuncio" as Anuncio

Vendedor -> Sistema : adicionarPreco(idAnuncio, preco)
Sistema -> Anuncio : setPreco(preco)
Anuncio --> Sistema : confirmado
Sistema --> Vendedor : preço adicionado
@enduml
```

## Alterar descrição

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : alterarDescricao(idAnuncio, novaDescricao)
Sistema -> Service : alterarDescricao(idAnuncio, novaDescricao)
Service -> Anuncio : setDescricao(novaDescricao)
Anuncio --> Service : confirmado
Service --> Sistema : sucesso
Sistema --> Vendedor : descrição atualizada
@enduml
```

## Alterar preço

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : alterarPreco(idAnuncio, novoPreco)
Sistema -> Service : alterarPreco(idAnuncio, novoPreco)
Service -> Anuncio : setPreco(novoPreco)
Anuncio --> Service : confirmado
Service --> Sistema : sucesso
Sistema --> Vendedor : preço atualizado
@enduml
```

## Adicionar motivo da exclusão

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : removerAnuncio(id, motivo)
Sistema -> Service : removerAnuncio(id, motivo)
Service -> Anuncio : registrarMotivo(motivo)
Anuncio --> Service : ok
Service -> Anuncio : marcarComoRemovido()
Anuncio --> Service : confirmado
Service --> Sistema : anúncio removido
Sistema --> Vendedor : confirmação
@enduml
```

## Visualizar detalhes

```plantuml
@startuml
actor Comprador
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Comprador -> Sistema : visualizarDetalhes(idAnuncio)
Sistema -> Service : obterDetalhes(idAnuncio)
Service -> Anuncio : getDetalhes()
Anuncio --> Service : dadosAnuncio
Service --> Sistema : dadosAnuncio
Sistema --> Comprador : exibirDetalhes
@enduml
```

## Acompanhar status

```plantuml
@startuml
actor Comprador
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Comprador -> Sistema : acompanharStatus(idAnuncio)
Sistema -> Service : consultarStatus(idAnuncio)
Service -> Anuncio : getStatus()
Anuncio --> Service : status
Service --> Sistema : status
Sistema --> Comprador : status do veículo
@enduml
```

## Criar perfil

```plantuml
@startuml
actor Usuario
participant "Sistema" as Sistema
participant "UsuarioService" as Service
participant "Usuario" as UsuarioClass

Usuario -> Sistema : criarPerfil(dadosPessoais)
Sistema -> Service : criarPerfil(dadosPessoais)
Service -> UsuarioClass : instanciarUsuario(dados)
UsuarioClass --> Service : novoUsuario
Service --> Sistema : perfilCriado
Sistema --> Usuario : confirmação de criação
@enduml
```

## Adicionar fotos

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : adicionarFotos(idAnuncio, fotos)
Sistema -> Service : adicionarFotos(idAnuncio, fotos)
Service -> Anuncio : anexarFotos(fotos)
Anuncio --> Service : fotos adicionadas
Service --> Sistema : sucesso
Sistema --> Vendedor : fotos adicionadas
@enduml
```

## Adicionar localização

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : adicionarLocalizacao(idAnuncio, endereco)
Sistema -> Service : adicionarLocalizacao(idAnuncio, endereco)
Service -> Anuncio : setLocalizacao(endereco)
Anuncio --> Service : ok
Service --> Sistema : localização adicionada
Sistema --> Vendedor : confirmação
@enduml
```

## Alterar fotos

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : alterarFotos(idAnuncio, novasFotos)
Sistema -> Service : alterarFotos(idAnuncio, novasFotos)
Service -> Anuncio : substituirFotos(novasFotos)
Anuncio --> Service : fotos atualizadas
Service --> Sistema : sucesso
Sistema --> Vendedor : fotos alteradas
@enduml
```

## Alterar localização

```plantuml
@startuml
actor Vendedor
participant "Sistema" as Sistema
participant "AnuncioService" as Service
participant "Anuncio" as Anuncio

Vendedor -> Sistema : alterarLocalizacao(idAnuncio, novoEndereco)
Sistema -> Service : alterarLocalizacao(idAnuncio, novoEndereco)
Service -> Anuncio : atualizarEndereco(novoEndereco)
Anuncio --> Service : endereço atualizado
Service --> Sistema : sucesso
Sistema --> Vendedor : localização atualizada
@enduml
```

## Excluir perfil

```plantuml
@startuml
actor Usuario
participant "Sistema" as Sistema
participant "UsuarioService" as Service
participant "Usuario" as UsuarioClass

Usuario -> Sistema : excluirPerfil(idUsuario)
Sistema -> Service : excluirPerfil(idUsuario)
Service -> UsuarioClass : marcarComoExcluido()
UsuarioClass --> Service : confirmado
Service --> Sistema : perfil excluído
Sistema --> Usuario : confirmação de exclusão
@enduml
```

