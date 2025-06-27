# Especificação de Casos de Uso - Sistema de Compra e Venda de Veículos

# UC001 - Negociar Condições de Venda

# Descrição

| Código / Nome do Caso de Uso | UC001 - Negociar Condições de Venda |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador/Vendedor |
| **Resumo**                  | Neste caso de uso, o comprador e o vendedor podem negociar os detalhes da venda, como preço e condições de pagamento, antes de concluir a transação. |
| **Pré-condições**           | O comprador e o vendedor devem estar autenticados no sistema. |
| **Pós-condições**           | As condições da venda são acordadas entre as partes. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador inicia a negociação com o vendedor. | |
| | 2. O sistema permite a troca de mensagens entre as partes (inclui UC002 - "Enviar Mensagens"). |
| 3. O vendedor pode aceitar ou sugerir novas condições. | |
| 4. O comprador pode aceitar ou rejeitar as novas condições. | |
| | 5. Quando um acordo é fechado, o sistema registra a negociação concluída. |

---

# Fluxo Alternativo - Sem acordo

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 4. | |
| 2. Caso o comprador e o vendedor não cheguem a um acordo, a negociação pode ser cancelada. | |

---

# UC002 - Enviar Mensagens

# Descrição

| Código / Nome do Caso de Uso | UC002 - Enviar Mensagens |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador/Vendedor |
| **Resumo**                  | Neste caso de uso, os compradores e vendedores podem trocar mensagens dentro da plataforma para discutir a negociação. |
| **Pré-condições**           | O comprador e o vendedor devem estar autenticados no sistema. |
| **Pós-condições**           | A mensagem é enviada e armazenada no histórico de conversa. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário acessa a opção de mensagens. | |
| | 2. O sistema exibe a conversa existente ou inicia uma nova. |
| 3. O usuário digita a mensagem e a envia. | |
| | 4. O sistema armazena a mensagem e a exibe para o destinatário. |

---

# Fluxo Alternativo - Falha no envio

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema detecta um erro na conexão e não envia a mensagem. |
| | 3. O sistema permite uma nova tentativa. |
| 4. O usuário pode tentar novamente. | |

---

# UC003 - Definir Veículo como Vendido

# Descrição

| Código / Nome do Caso de Uso | UC003 - Definir Veículo como Vendido |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode marcar um veículo como vendido após a finalização da negociação. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o veículo deve estar anunciado na plataforma. |
| **Pós-condições**           | O veículo é removido da lista de anúncios disponíveis e seu status é atualizado. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de gerenciamento de anúncios. | |
| 2. O vendedor seleciona o veículo e marca como vendido. | |
| | 3. A API de pagamento verifica o pagamento (inclui UC006 - "Verificar Pagamento"). |
| | 4. O sistema atualiza o status do veículo (inclui UC008 - "Alterar Status do Veículo"). |
| | 5. O sistema notifica a confirmação da venda (inclui UC007 - "Notificar Confirmação"). |

---

# UC004 - Consultar Histórico de Vendas

# Descrição

| Código / Nome do Caso de Uso | UC004 - Consultar Histórico de Vendas |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode acessar o histórico de veículos vendidos na plataforma. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema. |
| **Pós-condições**           | O histórico de vendas é exibido. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de histórico de vendas. | |
| | 2. O sistema exibe uma lista dos veículos vendidos. |
| 3. O vendedor pode visualizar detalhes específicos (extende UC009 - "Visualizar Detalhes por Venda"). | |

---

# UC005 - Consultar Histórico de Compras

# Descrição

| Código / Nome do Caso de Uso | UC005 - Consultar Histórico de Compras |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador |
| **Resumo**                  | Neste caso de uso, o comprador pode acessar o histórico de veículos adquiridos na plataforma. |
| **Pré-condições**           | O comprador deve estar autenticado no sistema. |
| **Pós-condições**           | O histórico de compras é exibido. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador acessa a opção de histórico de compras. | |
| | 2. O sistema exibe uma lista dos veículos adquiridos. |
| 3. O comprador pode visualizar detalhes específicos (extende UC012 - "Visualizar Detalhes por Compra"). | |

---

# UC006 - Verificar Pagamento

# Descrição

| Código / Nome do Caso de Uso | UC006 - Verificar Pagamento |
|-----------------------------|--------------------------------|
| **Ator Principal**          | API de Pagamento |
| **Resumo**                  | Neste caso de uso, a API de pagamento verifica a confirmação do pagamento antes de concluir a venda de um veículo. |
| **Pré-condições**           | O pagamento deve ter sido iniciado. |
| **Pós-condições**           | A API de pagamento confirma ou rejeita a transação com base no status do pagamento. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário realiza o pagamento. | |
| | 2. A API de pagamento verifica e retorna o status do pagamento. |
| | 3. A API de pagamento confirma ou rejeita o pagamento. |

---

# Fluxo Alternativo - Pagamento recusado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. A API de pagamento retorna que o pagamento foi recusado. |
| | 3. O sistema permite uma nova tentativa. |
| 4. O usuário pode tentar novamente. | |

---

# UC007 - Notificar Confirmação

# Descrição

| Código / Nome do Caso de Uso | UC007 - Notificar Confirmação |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Sistema |
| **Resumo**                  | Neste caso de uso, o sistema notifica o vendedor e o comprador sobre a conclusão da venda do veículo. |
| **Pré-condições**           | O veículo deve estar marcado como vendido. |
| **Pós-condições**           | O comprador e o vendedor recebem a notificação de confirmação. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| | 1. O sistema verifica o status do veículo. |
| | 2. O sistema envia uma notificação ao comprador e ao vendedor informando a finalização da venda. |

---

# Fluxo Alternativo - Falha na Notificação

| **Usuário** | **Sistema** |
|---------------|-------------|
| | 1. O sistema tenta enviar a notificação. |
| | 2. Caso ocorra uma falha no envio, o sistema armazena a notificação para nova tentativa posterior. |

---

# UC008 - Alterar Status do Veículo

# Descrição

| Código / Nome do Caso de Uso | UC008 - Alterar Status do Veículo |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Sistema |
| **Resumo**                  | Neste caso de uso, o sistema altera o status de um veículo quando ele é vendido. |
| **Pré-condições**           | O veículo deve estar cadastrado no sistema e marcado pelo vendedor como vendido. |
| **Pós-condições**           | O status do veículo é atualizado para "Vendido". |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| | 1. O sistema recebe a solicitação para alteração do status do veículo. |
| | 2. O sistema atualiza o status do veículo. |

---

# Fluxo Alternativo - Falha na Atualização

| **Usuário** | **Sistema** |
|---------------|-------------|
| | 1. O sistema tenta atualizar o status do veículo. |
| | 2. Caso ocorra um erro, o sistema registra a falha e não atualiza o status do veículo. |

---

# UC009 - Visualizar Detalhes por Venda

# Descrição

| Código / Nome do Caso de Uso | UC009 - Visualizar Detalhes por Venda |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode acessar os detalhes específicos de uma venda realizada. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e a venda deve existir. |
| **Pós-condições**           | Os detalhes da venda são exibidos. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de histórico de vendas. | |
| 2. O vendedor seleciona uma venda específica. | |
| | 3. O sistema exibe os detalhes da transação. |

---

# Fluxo Alternativo - Venda Não Encontrada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor tenta acessar os detalhes de uma venda. | |
| | 2. O sistema não encontra a venda. |
| | 3. O sistema retorna à opção de histórico de vendas. |

---

# UC010 - Gerenciar Usuários

# Descrição

| Código / Nome do Caso de Uso | UC010 - Gerenciar Usuários |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Admin |
| **Resumo**                  | Neste caso de uso, o administrador pode gerenciar os usuários cadastrados no sistema. |
| **Pré-condições**           | O administrador deve estar autenticado no sistema. |
| **Pós-condições**           | O usuário pode ser editado ou excluído. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O administrador acessa a opção de gerenciamento de usuários. | |
| | 2. O sistema exibe a lista de usuários cadastrados. |
| 3. O administrador pode visualizar, editar ou excluir um usuário. | |

---

# Fluxo Alternativo 1 - Erro na Edição/Exclusão

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O administrador tenta editar ou excluir um usuário. | |
| | 3. O sistema encontra um erro durante o processo de edição/exclusão. |
| | 4. O sistema retorna à opção de gerenciamento de usuários. |

---

# Fluxo Alternativo 2 - Usuário Não Encontrado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O administrador tenta gerenciar um usuário inexistente. | |
| | 3. O sistema informa que o usuário não foi encontrado. |
| | 4. O sistema retorna à opção de gerenciamento de usuários. |

---

# UC011 - Gerenciar Anúncios

# Descrição

| Código / Nome do Caso de Uso | UC011 - Gerenciar Anúncios |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Admin |
| **Resumo**                  | Neste caso de uso, o administrador pode gerenciar os anúncios publicados na plataforma. |
| **Pré-condições**           | O administrador deve estar autenticado no sistema. |
| **Pós-condições**           | Os anúncios podem ser removidos ou modificados. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O administrador acessa a opção de gerenciamento de anúncios. | |
| | 2. O sistema exibe a lista de anúncios ativos. |
| 3. O administrador pode visualizar, editar ou remover um anúncio. | |

---

# Fluxo Alternativo 1 - Erro na Edição/Exclusão

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O administrador tenta editar ou excluir um anúncio. | |
| | 3. O sistema encontra um erro durante o processo de edição/exclusão. |
| | 4. O sistema retorna à opção de gerenciamento de anúncios. |

---

# Fluxo Alternativo 2 - Anúncio Não Encontrado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O administrador tenta gerenciar um anúncio inexistente. | |
| | 3. O sistema informa que o anúncio não foi encontrado. |
| | 4. O sistema retorna à opção de gerenciamento de anúncios. |

---

# UC012 - Visualizar Detalhes por Compra

# Descrição

| Código / Nome do Caso de Uso | UC012 - Visualizar Detalhes por Compra |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador |
| **Resumo**                  | Neste caso de uso, o comprador pode acessar os detalhes específicos de uma compra realizada. |
| **Pré-condições**           | O comprador deve estar autenticado no sistema. |
| **Pós-condições**           | Os detalhes da compra são exibidos. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador acessa a opção de histórico de compras. | |
| 2. O comprador seleciona uma compra específica. | |
| | 3. O sistema exibe os detalhes da transação. |

---

# Fluxo Alternativo - Compra Não Encontrada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador tenta acessar os detalhes de uma compra. | |
| | 2. O sistema não encontra a compra. |
| | 3. O sistema retorna à opção de histórico de compras. |

---
