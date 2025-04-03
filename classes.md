# Diagrama de Classe

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

``` plantuml
@startuml 

class Usuário {
-id: int
-nome: String
-cpf: String
-email: String
-senha: String
-telefone: String
-tipo: String
-dataCadastro: Data
-statusConta: String
-endereço: Endereço

+editarPerfil(nome: String, cpf: String, email: String, senha: String, telefone: String): void
+excluirPerfil(): void
+fazerLogin(email: String, senha: String): boolean
#verificarSenha(senha: String): boolean
+alterarSenha(senhaAtual: String, novaSenha: String): boolean
+recuperarConta(email: String): boolean

}

class Comprador {

}

class Vendedor {

}

class Administrador {

}

Usuário <|-- Comprador
Usuário <|-- Vendedor
Usuário <|-- Administrador

class Data {
-dia: int
-mês: int
-ano: int

+exibirData(): void
}

class Endereço {
-logradouro: String
-número: int
-complemento: String
-cep: String
-bairro: String
-cidade: String
-estado: String
-país: String

+exibirEndereço(): void
}
 
@enduml
```