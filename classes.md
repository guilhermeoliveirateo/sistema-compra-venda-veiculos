# Diagrama de Classe

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

``` plantuml
@startuml 

class Usuario{
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

class Comprador{
-historicoCompras: List<Anuncio>
-veiculosAcompanhados: List<Anuncio>

+buscarVeiculo(descricao: String, preco: float): List<Anuncio>
+visualizarDetalhes(anuncioId: int): Anuncio
+consultarHistoricoCompras(): List<Anuncio>
+negociarCondicoes(vendedor: Vendedor, anuncio: Anuncio): void
+adicionarFavorito(anuncioId: int): void
+removerFavorito(anuncioId: int): void
}

class Vendedor{
-historicoVendas: List<Anuncio>
-listaAnuncios: List<Anuncio>

+removerAnuncio(anuncioId: int): void
+criarAnuncio(veiculo: Veiculo, descricao: String, preco: float): Anuncio
+editarAnuncio(anuncioId: int, novaDescricao: String, novoPreco: float): void
+definirComoVendido(anuncioId: int): void
+negociarCondicoes(comprador: Comprador, anuncio: Anuncio): void
+consultarHistoricoVendas(): List<Anuncio>
+criarVeiculo(tipo: String, marca: String, modelo: String, ano: int, km: int): Veiculo
+editarVeiculo(veiculoId: int, tipo: String, marca: String, modelo: String, ano: int, km: int): void
+removerVeiculo(veiculoId: int): void
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
-id: int
-tipo: String
-marca: String
-modelo: String
-ano: int
-quilometragem: int
-localizacao: Endereço
-status: String

+criarCarro(portas: int, combustivel: String, cambio: String, portaMalas: float, tetoSolar: boolean, ac: boolean): Carro
+editarCarro(carroId: int, portas: int, combustivel: String, cambio: String, portaMalas: float, tetoSolar: boolean, ac: boolean): void
+criarMoto(cilindradas: int, freio: String, tipoMoto: String, partidaEletrica: boolean, abs: boolean): Moto
+editarMoto(motoId: int, cilindradas: int, freio: String, tipoMoto: String, partidaEletrica: boolean, abs: boolean): void
+criarCaminhao(carga: float, eixos: int, carroceria: String, freiosAr: boolean, leito: boolean): Caminhao
+editarCaminhao(caminhaoId: int, carga: float, eixos: int, carroceria: String, freiosAr: boolean, leito: boolean): void
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
-id: int
-veiculo: Veiculo
-vendedor: Vendedor
-descricao: String
-preco: float
-dataCriacao: Data
-status: String

+ativarAnuncio(anuncioId: int): void
+desativarAnuncio(anuncioId: int): void
}

class Pagamento{
-id: int
-comprador: Comprador
-vendedor: Vendedor
-valor: float
-dataPagamento: Data
-status: String

+verificarPagamento(pagamentoId: int): boolean
+confirmarPagamento(): void
}

class HistoricoTransacoes{
-id: int
-usuario: Usuario
-tipo: String

+consultarHistorico(usuario: Usuario, tipo: String): List<HistoricoTransacoes>
}

class Mensagem{
-id: int
-remetente: Usuario
-destinatario: Usuario
-conteudo: String
-dataEnvio: Data

+enviarMensagem(destinatario: Usuario, conteudo: String): void
}

class Negociacao{
-id: int
-comprador: Comprador
-vendedor: Vendedor
-anuncio: Anuncio
-status: String

+iniciarNegociacao(comprador: Comprador, vendedor: Vendedor, anuncio: Anuncio): void
+encerrarNegociacao(negociacaoId: int): void
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

Comprador --> "0..*" HistoricoTransacoes
Vendedor --> "0..*" Anuncio
Vendedor --> "0..*" HistoricoTransacoes
Comprador --> "0..*" Mensagem
Vendedor --> "0..*" Mensagem
Comprador --> "0..*" Pagamento
Vendedor --> "0..*" Pagamento
Anuncio --> Veiculo
Anuncio --> Vendedor
Negociacao --> Comprador
Negociacao --> Vendedor
Negociacao --> Veiculo
Negociacao --> "0..*" Mensagem
HistoricoTransacoes --> Veiculo
HistoricoTransacoes --> Usuario
Pagamento --> Comprador
Pagamento --> Vendedor
Mensagem --> Usuario
 
@enduml
```