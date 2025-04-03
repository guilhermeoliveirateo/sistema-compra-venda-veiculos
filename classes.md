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
-email: String
-senha: String
-telefone: String
-tipo: String
-dataCadastro: Date

+editarPerfil(nome: String, email: String, senha: String, telefone: String): void
+excluirPerfil(): void
+fazerLogin(email: String, senha: String): boolean
#verificarSenha(senha: String): boolean

}
 
@enduml
```