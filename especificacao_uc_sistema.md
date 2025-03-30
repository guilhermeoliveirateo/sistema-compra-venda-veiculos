# Especificação de Casos de Uso - Sistema de Compra e Venda de Veículos

# Grupo

- Guilherme Teodoro de Oliveira RA: 10425362
- Luís Henrique Ribeiro Fernandes RA: 10420079
- Vinícius Brait Lorimier RA: 10420046

# UC001 - Fazer Login

# Descrição

| Código / Nome do Caso de Uso | UC001 - Fazer Login |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador/Vendedor |
| **Resumo**                  | Neste caso de uso, o usuário realiza o login na plataforma informando suas credenciais (e-mail e senha). Caso a senha esteja incorreta, uma mensagem de erro será exibida. |
| **Pré-condições**           | O usuário deve estar cadastrado na plataforma. |
| **Pós-condições**           | O usuário é autenticado e tem acesso ao sistema. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário acessa a tela de login. | |
| | 2. O sistema solicita e-mail e senha. |
| 3. O usuário informa as credenciais. | |
| | 4. O sistema verifica a senha (inclui UC007 - "Verificar senha"). |
| | 5. Se as credenciais forem válidas, o sistema autentica o usuário e redireciona para a página inicial. |

---

# Fluxo Alternativo - Senha incorreta

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 4. | |
| | 2. O sistema verifica que a senha está incorreta. |
| | 3. O sistema exibe uma mensagem de erro (estende UC008 - "Exibir mensagem de erro"). | |
| 4. O usuário pode tentar novamente. |

---