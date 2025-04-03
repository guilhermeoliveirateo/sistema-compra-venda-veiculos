# Diagrama de Classe

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

``` plantuml
@startuml 

class Usuario {
-id: int
-nome: String
-cpf: String
-email: String
-senha: String
-telefone: String
-tipo: String
-dataCadastro: Data
-statusConta: String
-endereco: Endereco

+editarPerfil(nome: String, email: String, senha: String, telefone: String, endereco: Endereco): void
+excluirPerfil(): void
+fazerLogin(email: String, senha: String): boolean
#verificarSenha(senha: String): boolean
+alterarSenha(senhaAtual: String, novaSenha: String): boolean
+recuperarConta(email: String): boolean
}

class Comprador {
-historicoCompras: List<Veiculo>
-veiculosAcompanhados: List<Veículo>

+buscarVeiculo(tipo: String, marca: String, modelo: String, ano: int, preco: float): List<Veículo>
+visualizarDetalhes(veiculoId: int): Veiculo
+consultarHistoricoCompras(): List<Veículo>
+negociarCondicoes(vendedor: Vendedor, veiculo: Veiculo): void
+adicionarFavorito(veiculoId: int): void
+removerFavorito(veiculoId: int): void
}

class Vendedor {
-historicoVendas: List<Veiculo>
-listaAnuncios: List<Anuncio>

+removerAnuncio(anuncioId: int): void
+criarAnuncio(veiculoId: int): void
+definirComoVendido(veiculoId: int): void
+negociarCondicoes(comprador: Comprador, veiculo: Veiculo): void

}

class Administrador {
-adminId: int

+gerenciarAnuncios(listaAnuncios: List<Anuncio>): void
+gerenciarUsuarios(listaUsuarios: List<Usuario>): void
+suspenderConta(usuarioId: int): void
+reativarConta(usuarioId: int): void
+suspenderAnuncio(anuncioId: int): void
+reativarAnuncio(anuncioId: int): void
}

Usuario <|-- Comprador
Usuario <|-- Vendedor
Usuario <|-- Administrador

class Veiculo {
-id: int
-tipo: String
-marca: String
-modelo: String
-ano: int
-preco: float
-quilometragem: int
-localizacao: Endereço
-status: String
-descricao: String

}

class Carro {
}

class Moto {
}

class Caminhao {
}

Veiculo <|-- Carro
Veiculo <|-- Moto
Veiculo <|-- Caminhao

class Anuncio {

}

class Data {
-dia: int
-mes: int
-ano: int

+exibirData(): void
}

class Endereco {
-logradouro: String
-numero: int
-complemento: String
-cep: String
-bairro: String
-cidade: String
-estado: String
-pais: String

+exibirEndereco(): void
}
 
@enduml
```