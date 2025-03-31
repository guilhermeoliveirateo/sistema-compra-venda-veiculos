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
| | 3. O sistema exibe uma mensagem de erro (estende UC008 - "Exibir mensagem de erro"). |
| 4. O usuário pode tentar novamente. | |

---

# UC002 - Editar Perfil

# Descrição

| Código / Nome do Caso de Uso | UC002 - Editar Perfil |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador/Vendedor |
| **Resumo**                  | Neste caso de uso, o usuário pode editar informações do seu perfil. |
| **Pré-condições**           | O usuário deve estar autenticado no sistema. |
| **Pós-condições**           | O perfil do usuário é atualizado com as novas informações. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário acessa a opção de editar perfil. | |
| | 2. O sistema exibe as informações atuais do perfil. |
| 3. O usuário altera os dados desejados. | |
| | 4. O sistema salva as alterações. |

---

# Fluxo Alternativo - Cancelamento da edição

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O usuário decide não editar o perfil e cancela a operação. | |
| | 3. O sistema retorna à opção de editar perfil sem alterações. |

---

# UC003 - Criar Anúncio

# Descrição

| Código / Nome do Caso de Uso | UC003 - Criar Anúncio |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode criar um anúncio para vender um veículo, informando descrição, preço, fotos e localização. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema. |
| **Pós-condições**           | O anúncio é criado e publicado na plataforma. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de criar anúncio. | |
| | 2. O sistema exibe um formulário para preenchimento dos dados. |
| 3. O vendedor adiciona a descrição (inclui UC009 - "Adicionar descrição"). | |
| 4. O vendedor define o preço (inclui UC010 - "Adicionar preço do veículo"). | |
| 5. O vendedor adiciona fotos (inclui UC017 - "Adicionar fotos"). | |
| 6. O vendedor informa a localização (inclui UC018 - "Adicionar localização"). | |
| | 7. O sistema salva os dados e publica o anúncio. |

---

# Fluxo Alternativo - Cancelamento da criação

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 6. | |
| 2. O vendedor decide não criar o anúncio e cancela a operação. | |
| | 3. O sistema retorna à lista de anúncios sem alterações. |

---

# UC004 - Editar Anúncio

# Descrição

| Código / Nome do Caso de Uso | UC004 - Editar Anúncio |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode editar um anúncio já publicado, alterando descrição, preço, fotos e localização. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar ativo. |
| **Pós-condições**           | As informações do anúncio são atualizadas. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a lista de anúncios. | |
| 2. O vendedor seleciona um anúncio para edição. | |
| | 3. O sistema exibe os dados do anúncio. |
| 4. O vendedor pode alterar a descrição (estende UC011 - "Alterar descrição"). | |
| 5. O vendedor pode alterar o preço (estende UC012 - "Alterar preço"). | |
| 6. O vendedor pode alterar as fotos (estende UC019 - "Alterar fotos"). | |
| 7. O vendedor pode alterar a localização (estende UC020 - "Alterar localização"). | |
| | 8. O sistema salva as alterações. |

---

# Fluxo Alternativo - Cancelamento da edição

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 7. | |
| 2. O vendedor decide não editar o anúncio e cancela a operação. | |
| | 3. O sistema retorna à lista de anúncios sem alterações. |

---

# UC005 - Remover Anúncio

# Descrição

| Código / Nome do Caso de Uso | UC005 - Remover Anúncio |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode excluir um anúncio de sua conta, informando o motivo da exclusão. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar ativo. |
| **Pós-condições**           | O anúncio é removido do sistema. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a lista de anúncios. | |
| 2. O vendedor seleciona um anúncio para remoção. | |
| | 3. O sistema solicita o motivo da exclusão (inclui UC013 - "Adicionar motivo da exclusão"). |
| 4. O vendedor informa o motivo e confirma a exclusão. | |
| | 5. O sistema remove o anúncio da plataforma. |

---

# Fluxo Alternativo - Cancelamento da remoção

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor decide não remover o anúncio e cancela a operação. | |
| | 3. O sistema retorna à lista de anúncios sem alterações. |

---

# UC006 - Buscar Veículo

# Descrição

| Código / Nome do Caso de Uso | UC006 - Buscar Veículo |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador |
| **Resumo**                  | Neste caso de uso, o comprador pode buscar veículos disponíveis na plataforma usando filtros como descrição, preço e localização. |
| **Pré-condições**           | O comprador deve estar autenticado no sistema. |
| **Pós-condições**           | O comprador visualiza uma lista de veículos compatíveis com sua busca. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador acessa a opção de busca. | |
| 2. O comprador define os filtros desejados. | |
| | 3. O sistema exibe uma lista de veículos correspondentes. |

---

# Fluxo Alternativo - Nenhum veículo encontrado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema informa que não há veículos compatíveis. |
| 3. O comprador pode ajustar os filtros e tentar novamente. | |

---