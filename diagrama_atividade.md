# Diagrama de Atividades

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046


``` plantuml
@startuml

|Usuário|
start
:Realizar Login;
if (Login válido?) then (Sim)
    :Acessar sistema;
else (Não)
    :Exibir mensagem de erro;
    stop
endif

partition Perfil {
    if (Perfil existente?) then (Sim)
        :Editar perfil;
        :Excluir perfil;
    else (Não)
        :Criar perfil;
    endif
}

partition Anúncio {
    if (É vendedor?) then (Sim)
        :Criar anúncio;
        fork
            :Adicionar descrição;
            :Adicionar fotos;
            :Adicionar localização;
            :Adicionar preço;
        fork again
            :Editar anúncio;
            :Alterar descrição;
            :Alterar fotos;
            :Alterar localização;
            :Alterar preço;
            :Remover anúncio (se desejar);
        end fork
    endif
}

partition Compra {
    if (É comprador?) then (Sim)
        :Buscar veículo;
        :Visualizar detalhes;
        :Negociar condições de venda;
        :Enviar mensagens;
    endif
}

partition Venda {
    if (Negociação concluída?) then (Sim)
        :Definir veículo como vendido;
        :Verificar pagamento;
        if (Pagamento confirmado?) then (Sim)
            :Alterar status do veículo;
            :Notificar confirmação;
        else (Não)
            :Cancelar venda;
        endif
    endif
}

partition Histórico {
    :Consultar histórico de compras;
    :Consultar histórico de vendas;
}

partition Administração {
    :Gerenciar usuários;
    :Gerenciar anúncios;
}

stop

@enduml
```