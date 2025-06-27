# Diagrama de Classe

``` plantuml
@startuml 

class Usuario{
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
+excluirPerfil(usuario: Usuario): void
+fazerLogin(email: String, senha: String): boolean
#verificarSenha(senha: String): boolean
+alterarSenha(senhaAtual: String, novaSenha: String): boolean
+recuperarConta(email: String): boolean
}

class Comprador{
-historicoCompras: List<Anuncio>
-veiculosAcompanhados: List<Anuncio>

+buscarVeiculo(descricao: String, preco: float): List<Anuncio>
+visualizarDetalhes(anuncio: Anuncio): Anuncio
+consultarHistoricoCompras(): List<Anuncio>
+negociarCondicoes(vendedor: Vendedor, anuncio: Anuncio): void
+adicionarFavorito(anuncio: Anuncio): void
+removerFavorito(anuncio: Anuncio): void
}

class Vendedor{
-historicoVendas: List<Anuncio>
-listaAnuncios: List<Anuncio>

+removerAnuncio(anuncio: Anuncio): void
+criarAnuncio(veiculo: Veiculo, descricao: String, preco: float): Anuncio
+editarAnuncio(novaDescricao: String, novoPreco: float): void
+definirComoVendido(anuncio: Anuncio): void
+negociarCondicoes(comprador: Comprador, anuncio: Anuncio): void
+consultarHistoricoVendas(): List<Anuncio>
+criarVeiculo(tipo: String, marca: String, modelo: String, ano: int, km: int): Veiculo
+editarVeiculo(tipo: String, marca: String, modelo: String, ano: int, km: int): void
+removerVeiculo(veiculo: Veiculo): void
}

class Administrador{
-numeroFuncionario: int

+gerenciarAnuncios(listaAnuncios: List<Anuncio>): void
+gerenciarUsuarios(listaUsuarios: List<Usuario>): void
}

Usuario <|-- Comprador
Usuario <|-- Vendedor
Usuario <|-- Administrador

class Veiculo{
-tipo: String
-marca: String
-modelo: String
-ano: int
-quilometragem: int
-localizacao: Endereço
-status: String

+criarCarro(portas: int, combustivel: String, cambio: String, portaMalas: float, tetoSolar: boolean, ac: boolean): Carro
+editarCarro(portas: int, combustivel: String, cambio: String, portaMalas: float, tetoSolar: boolean, ac: boolean): void
+criarMoto(cilindradas: int, freio: String, tipoMoto: String, partidaEletrica: boolean, abs: boolean): Moto
+editarMoto(cilindradas: int, freio: String, tipoMoto: String, partidaEletrica: boolean, abs: boolean): void
+criarCaminhao(carga: float, eixos: int, carroceria: String, freiosAr: boolean, leito: boolean): Caminhao
+editarCaminhao(carga: float, eixos: int, carroceria: String, freiosAr: boolean, leito: boolean): void
}

class Carro{
-qtdPortas: int
-tipoCombustivel: String
-cambio: String
-capacidadePortaMalas: float
-tetoSolar: boolean
-arCondicionado: boolean

+exibirInformacoesCarro(): void
}

class Moto{
-cilindradas: int
-tipoFreio: String
-tipoMoto: String
-partidaEletrica: boolean
-abs: boolean

+exibirInformacoesMoto(): void
}

class Caminhao{
-capacidadeCarga: float
-eixos: int
-tipoCarroceria: String
-freiosAr: boolean
-cabineLeito: boolean

+exibirInformacoesCaminhao(): void
}

Veiculo <|-- Carro
Veiculo <|-- Moto
Veiculo <|-- Caminhao

class Anuncio{
-veiculo: Veiculo
-vendedor: Vendedor
-descricao: String
-preco: float
-dataCriacao: Data
-status: String

+ativarAnuncio(anuncio: Anuncio): void
+desativarAnuncio(anuncio: Anuncio): void
}

class Pagamento{
-comprador: Comprador
-vendedor: Vendedor
-valor: float
-dataPagamento: Data
-status: String

+verificarPagamento(pagamento: Pagamento): boolean
+confirmarPagamento(): void
}

class HistoricoTransacoes{
-usuario: Usuario
-tipo: String

+consultarHistorico(usuario: Usuario, tipo: String): List<HistoricoTransacoes>
}

class Mensagem{
-remetente: Usuario
-destinatario: Usuario
-conteudo: String
-dataEnvio: Data

+enviarMensagem(destinatario: Usuario, conteudo: String): void
}

class Negociacao{
-comprador: Comprador
-vendedor: Vendedor
-anuncio: Anuncio
-status: String

+iniciarNegociacao(comprador: Comprador, vendedor: Vendedor, anuncio: Anuncio): void
+encerrarNegociacao(negociacao: Negociacao): void
}

class Data{
-dia: int
-mes: int
-ano: int

+exibirData(): void
}

class Endereco{
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

Comprador "0..*" -- "0..*" HistoricoTransacoes
Vendedor "0..*" -- "0..*" Anuncio
Vendedor "0..*" -- "0..*" HistoricoTransacoes
Comprador "0..*" -- "0..*" Mensagem
Vendedor "0..*" -- "0..*" Mensagem
Comprador "0..*" -- "0..*" Pagamento
Vendedor "0..*" -- "0..*" Pagamento
Anuncio "1" -- "1" Veiculo
Anuncio "1" -- "1" Vendedor
Negociacao "1" -- "1" Comprador
Negociacao "1" -- "1" Vendedor
Negociacao "1" -- "1" Veiculo
Negociacao "0..*" -- "0..*" Mensagem
HistoricoTransacoes "1" -- "1" Veiculo
HistoricoTransacoes "1" -- "1" Usuario
Pagamento "1" -- "1" Comprador
Pagamento "1" -- "1" Vendedor
Mensagem "1" -- "1" Usuario
Mensagem "1" -- "1" Usuario
 
@enduml
```
