# Especificação de Casos de Uso - Sistema de Compra e Venda de Veículos

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

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