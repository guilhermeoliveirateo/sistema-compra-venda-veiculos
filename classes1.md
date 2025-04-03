'''
@startuml
' Definição das classes principais
class Usuario {
    - id: int
    - nome: string
    - email: string
    - senha: string
    - telefone: string
    - tipo: string
    - dataCadastro: date
    - statusConta: string
    + editarPerfil(nome: string, email: string, telefone: string): void
    + excluirPerfil(): void
    + fazerLogin(email: string, senha: string): bool
    # verificarSenha(senha: string): bool
    + alterarSenha(senhaAtual: string, novaSenha: string): bool
    + recuperarConta(email: string): bool
}

class Comprador {
    - historicoCompras: List<Veiculo>
    - favoritos: List<Veiculo>
    - enderecoEntrega: string
    - notificacoes: List<string>
    - metodoPagamentoPadrao: string
    + buscarVeiculo(filtro: string): List<Veiculo>
    + visualizarDetalhes(veiculoId: int): Veiculo
    + negociarCondicoes(vendedor: Vendedor, veiculo: Veículo): void
    + consultarHistoricoCompras(): List<Veiculo>
    + adicionarFavorito(veiculo: Veiculo): void
    + removerFavorito(veiculoId: int): void
    + avaliarVendedor(vendedor: Vendedor, nota: int, comentario: string): void
    + receberNotificacoes(): List<string>
}

class Vendedor {
    - historicoVendas: List<Anuncio>
    - listaAnuncios: List<Anuncio>
    - reputacao: float
    - carteiraVirtual: float
    - enderecoLoja: string
    + criarAnuncio(veiculo: Veiculo, descricao: string, preco: float): Anuncio
    + editarAnuncio(anuncioId: int, novaDescricao: string, novoPreco: float): void
    + removerAnuncio(anuncioId: int): void
    + definirComoVendido(veiculoId: int): void
    + consultarHistoricoVendas(): List<Anuncio>
    + responderNegociacao(comprador: Comprador, mensagem: string): void
    + sacarSaldo(valor: float): bool
    + alterarEnderecoLoja(novoEndereco: string): void
    + visualizarFeedbacks(): List<string>
}

class Administrador {
    - listaUsuarios: List<Usuario>
    - listaAnuncios: List<Anuncio>
    - relatoriosSistema: List<string>
    + gerenciarUsuarios(usuarios: List<Usuario>): void
    + gerenciarAnuncios(anuncios: List<Anuncio>): void
    + suspenderConta(usuarioId: int, motivo: string): void
    + reativarConta(usuarioId: int): void
    + analisarDenuncias(): List<string>
    + gerarRelatorios(tipo: string): string
    + visualizarMetricas(): string
}

class Veiculo {
    - id: int
    - tipo: string
    - marca: string
    - modelo: string
    - ano: int
    - preco: float
    - quilometragem: int
    - localizacao: string
    - fotos: List<string>
    - status: string
    + alterarPreco(novoPreco: float): void
    + alterarDescricao(novaDescricao: string): void
    + alterarFotos(novasFotos: List<string>): void
    + alterarLocalizacao(novaLocalizacao: string): void
}

class Carro {
    - qtdPortas: int
    - tipoCombustivel: string
    - cambio: string
    - capacidadePortaMalas: float
    - tetoSolar: bool
    - arCondicionado: bool
    + exibirInformacoesCarro(): string
    + calcularAutonomia(consumoMedio: float, capacidadeTanque: float): float
}

class Moto {
    - cilindradas: int
    - partidaEletrica: bool
    - tipoFreio: string
    - abs: bool
    - tipoMoto: string
    + exibirInformacoesMoto(): string
    + verificarSeguroObrigatorio(): bool
}

class Caminhao {
    - capacidadeCarga: float
    - eixos: int
    - tipoCarroceria: string
    - freiosAr: bool
    - cabineLeito: bool
    + exibirInformacoesCaminhao(): string
    + calcularAutonomiaCaminhao(consumoMedio: float, capacidadeTanque: float): float
}

class Anuncio {
    - id: int
    - veiculo: Veiculo
    - vendedor: Vendedor
    - descricao: string
    - preco: float
    - dataCriacao: date
    - status: string
    + ativarAnuncio(): void
    + desativarAnuncio(): void
    + adicionarDescricao(descricao: string): void
    + adicionarFotos(fotos: List<string>): void
}

class Pagamento {
    - id: int
    - comprador: Comprador
    - vendedor: Vendedor
    - valor: float
    - dataPagamento: date
    - status: string
    + verificarPagamento(): bool
    + confirmarPagamento(): void
}

class HistoricoTransacoes {
    - id: int
    - usuario: Usuario
    - tipo: string
    - veiculo: Veiculo
    - data: date
    - status: string
    + registrarTransacao(usuario: Usuario, veiculo: Veiculo, tipo: string): void
    + consultarHistorico(usuario: Usuario): List<HistoricoTransacoes>
}

class Mensagem {
    - id: int
    - remetente: Usuario
    - destinatario: Usuario
    - conteudo: string
    - dataEnvio: datetime
    + enviarMensagem(): void
    + receberMensagem(): string
}

class Negociacao {
    - id: int
    - comprador: Comprador
    - vendedor: Vendedor
    - veiculo: Veiculo
    - status: string
    - mensagens: List<Mensagem>
    + iniciarNegociacao(): void
    + encerrarNegociacao(): void
}

' Relacionamentos
Usuario <|-- Comprador
Usuario <|-- Vendedor
Usuario <|-- Administrador

Veiculo <|-- Carro
Veiculo <|-- Moto
Veiculo <|-- Caminhao

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
'''