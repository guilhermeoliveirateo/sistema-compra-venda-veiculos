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

# UC007 - Verificar Senha

# Descrição

| Código / Nome do Caso de Uso | UC007 - Verificar Senha |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Sistema |
| **Resumo**                  | Neste caso de uso, ocorre a verificação se a senha fornecida pelo usuário corresponde à senha armazenada no sistema. |
| **Pré-condições**           | O usuário deve ter informado um e-mail cadastrado na plataforma. |
| **Pós-condições**           | O sistema confirma a senha ou informa que ela está incorreta. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário insere o e-mail e senha. | |
| | 2. O sistema verifica se a senha está correta. |
| | 3. Se correta, o sistema permite o login. |

---

# Fluxo Alternativo - Senha incorreta

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| | 2. O sistema detecta que a senha está incorreta. |
| | 3. O sistema exibe uma mensagem de erro (estende UC008 - "Exibir mensagem de erro"). |
| 4. O usuário pode tentar novamente. | |

---

# UC008 - Exibir Mensagem de Erro

# Descrição

| Código / Nome do Caso de Uso | UC008 - Exibir Mensagem de Erro |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Sistema |
| **Resumo**                  | Neste caso de uso, ocorre a exibição de uma mensagem de erro para informar o usuário sobre problemas encontrados na senha informada. |
| **Pré-condições**           | O usuário inseriu uma senha incorreta para realizar o login. |
| **Pós-condições**           | O usuário recebe uma mensagem de erro sobre a senha incorreta. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| | 1. O sistema detecta um erro na senha informada pelo usuário durante o login. |
| | 2. O sistema exibe uma mensagem de senha incorreta. |

---

# UC009 - Adicionar Descrição

# Descrição

| Código / Nome do Caso de Uso | UC009 - Adicionar Descrição |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor deve adicionar uma descrição ao criar um anúncio de veículo. |
| **Pré-condições**           | O vendedor está criando um anúncio. |
| **Pós-condições**           | A descrição é adicionada ao anúncio. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de criar anúncio. | |
| 2. O vendedor insere a descrição do veículo. | |
| | 3. O sistema salva a descrição no anúncio. |

---

# Fluxo Alternativo 1 - Descrição inválida

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| | 2. O sistema detecta que a descrição é inválida. |
| | 3. O sistema solicita uma nova descrição. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma descrição adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor não adiciona uma descrição. | |
| | 3. O sistema solicita uma descrição. |
| 4. O vendedor pode tentar novamente. | |

---

# UC010 - Adicionar Preço do Veículo

# Descrição

| Código / Nome do Caso de Uso | UC010 - Adicionar Preço do Veículo |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor deve adicionar um preço de venda ao criar um anúncio de veículo. |
| **Pré-condições**           | O vendedor está criando um anúncio. |
| **Pós-condições**           | O preço do veículo é adicionado no anúncio. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor insere o valor do veículo. | |
| | 2. O sistema salva o preço no anúncio. |

---

# Fluxo Alternativo 1 - Preço inválido

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 1. | |
| | 2. O sistema detecta que o preço do veículo é inválido. |
| | 3. O sistema solicita um novo preço. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhum preço adicionado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 1. | |
| 2. O vendedor não adiciona um preço. | |
| | 3. O sistema solicita um preço. |
| 4. O vendedor pode tentar novamente. | |

---

# UC011 - Alterar Descrição

# Descrição

| Código / Nome do Caso de Uso | UC011 - Alterar Descrição |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode modificar a descrição de um anúncio já publicado. |
| **Pré-condições**           | O vendedor possui um anúncio ativo na plataforma. |
| **Pós-condições**           | A descrição do anúncio é atualizada. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de editar anúncio. | |
| 2. O vendedor modifica a descrição. | |
| | 3. O sistema salva as alterações. |

---

# Fluxo Alternativo 1 - Descrição inválida

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| | 2. O sistema detecta que a descrição é inválida. |
| | 3. O sistema solicita uma nova descrição. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma descrição adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor não adiciona uma nova descrição. | |
| | 3. O sistema solicita uma descrição. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 3 - Não alterar descrição

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor decide não modificar a descrição. | |
| | 3. O sistema retorna à opção de editar anúncio sem alterações. |
| 4. O vendedor pode continuar alterando os outros campos do anúncio. | |

---

# UC012 - Alterar Preço

# Descrição

| Código / Nome do Caso de Uso | UC012 - Alterar Preço |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode modificar o preço de um veículo já anunciado. |
| **Pré-condições**           | O vendedor possui um anúncio ativo na plataforma. |
| **Pós-condições**           | O preço do veículo é atualizado. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de editar anúncio. | |
| 2. O vendedor altera o preço. | |
| | 3. O sistema salva as alterações. |

---

# Fluxo Alternativo 1 - Preço inválido

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| | 2. O sistema detecta que o preço é inválido. |
| | 3. O sistema solicita um novo preço. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhum preço adicionado

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor não adiciona um novo preço. | |
| | 3. O sistema solicita um novo preço. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 3 - Não alterar preço

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor decide não modificar o preço. | |
| | 3. O sistema retorna à opção de editar anúncio sem alterações. |
| 4. O vendedor pode continuar alterando os outros campos do anúncio. | |

---

# UC013 - Adicionar Motivo da Exclusão

# Descrição

| Código / Nome do Caso de Uso | UC013 - Adicionar Motivo da Exclusão |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor deve informar um motivo ao excluir um anúncio. |
| **Pré-condições**           | O vendedor decidiu excluir um anúncio. |
| **Pós-condições**           | O motivo da exclusão é registrado. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de excluir anúncio. | |
| | 2. O sistema solicita o motivo da exclusão. |
| 3. O vendedor insere o motivo e confirma a exclusão. | |

---

# Fluxo Alternativo - Não remover anúncio

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 2. | |
| 2. O vendedor decide não excluir o anúncio. | |
| | 3. O sistema retorna à lista de anúncios sem alterações. |

---

# UC014 - Visualizar Detalhes

# Descrição

| Código / Nome do Caso de Uso | UC014 - Visualizar Detalhes |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador |
| **Resumo**                  | Neste caso de uso, o comprador pode visualizar os detalhes de um veículo anunciado. |
| **Pré-condições**           | O comprador acessa um anúncio. |
| **Pós-condições**           | O sistema exibe todas as informações do veículo. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador acessa um anúncio. | |
| | 2. O sistema exibe os detalhes do veículo. |

---

# UC015 - Acompanhar Status

# Descrição

| Código / Nome do Caso de Uso | UC015 - Acompanhar Status |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador |
| **Resumo**                  | Neste caso de uso, o comprador pode acompanhar o status do veículo. |
| **Pré-condições**           | O comprador demonstrou interesse em um anúncio. |
| **Pós-condições**           | O comprador pode visualizar o status atualizado do veículo. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O comprador acessa a opção de acompanhar status. | |
| | 2. O sistema exibe o status atual da negociação. |

---

# UC016 - Criar Perfil

# Descrição

| Código / Nome do Caso de Uso | UC016 - Criar Perfil |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Comprador/Vendedor |
| **Resumo**                  | Neste caso de uso, o usuário pode criar um perfil na plataforma. |
| **Pré-condições**           | O usuário deseja utilizar o sistema. |
| **Pós-condições**           | O perfil do usuário é criado. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O usuário acessa a opção de cadastro. | |
| | 2. O sistema solicita informações pessoais. |
| 3. O usuário preenche os dados. | |
| 4. O usuário confirma a criação do perfil. | |
| | 5. O sistema cria o perfil. |

---

# Fluxo Alternativo 1 - Cancelamento da criação

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O usuário decide não criar o perfil. | |
| | 3. O sistema retorna à opção de cadastro sem alterações. |

---

# Fluxo Alternativo 2 - Perfil já existe

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 4. | |
| | 2. O sistema identifica que o perfil já existe e não cria um novo. |
| | 3. O sistema retorna à tela de login. |
| 4. O usuário pode fazer o login em seu perfil. | |

---

# UC017 - Adicionar Fotos

# Descrição

| Código / Nome do Caso de Uso | UC017 - Adicionar Fotos |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor deve adicionar fotos ao seu anúncio de veículo para melhor apresentação aos compradores. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar em processo de criação. |
| **Pós-condições**           | As fotos são adicionadas ao anúncio e ficam visíveis para os compradores. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de adicionar fotos ao anúncio. | |
| | 2. O sistema exibe a interface para upload de imagens. |
| 3. O vendedor seleciona as fotos desejadas. | |
| | 4. O sistema valida e armazena as imagens. |
| | 5. O sistema confirma a adição das fotos ao anúncio. |

---

# Fluxo Alternativo 1 - Formato inválido

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema detecta que o formato da imagem não é aceito. |
| | 3. O sistema solicita novas imagens. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma foto adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor não adiciona novas imagens. | |
| | 3. O sistema solicita pelo menos uma imagem. |
| 4. O vendedor pode tentar novamente. | |

---

# UC018 - Adicionar Localização

# Descrição

| Código / Nome do Caso de Uso | UC018 - Adicionar Localização |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor deve adicionar a localização do veículo ao anúncio para que os compradores saibam onde ele está disponível. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar em processo de criação. |
| **Pós-condições**           | A localização é adicionada ao anúncio e exibida para os compradores. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de adicionar localização ao anúncio. | |
| | 2. O sistema exibe um campo para inserir a localização. |
| 3. O vendedor informa a localização do veículo. | |
| | 4. O sistema valida os dados e armazena a informação. |
| | 5. O sistema confirma a adição da localização ao anúncio. |

---

# Fluxo Alternativo 1 - Localização inválida

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema detecta que a localização inserida não é válida. |
| | 3. O sistema solicita uma nova localização. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma localização adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor não adiciona uma localização. | |
| | 3. O sistema solicita uma localização. |
| 4. O vendedor pode tentar novamente. | |

---

# UC019 - Alterar Fotos

# Descrição

| Código / Nome do Caso de Uso | UC019 - Alterar Fotos |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode alterar as fotos de um anúncio existente para atualizar a apresentação do veículo. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar em processo de edição. |
| **Pós-condições**           | As fotos do anúncio são atualizadas. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de editar o anúncio. | |
| | 2. O sistema exibe as fotos atuais do anúncio. |
| 3. O vendedor remove ou substitui as fotos desejadas. | |
| | 4. O sistema valida e armazena as novas imagens. |
| | 5. O sistema confirma a atualização das fotos. |

---

# Fluxo Alternativo 1 - Formato inválido

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema detecta que o formato da imagem não é aceito. |
| | 3. O sistema solicita novas imagens. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma foto adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor não adiciona novas imagens. | |
| | 3. O sistema solicita pelo menos uma imagem. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 3 - Não alterar fotos

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor decide não modificar as fotos. | |
| | 3. O sistema retorna à opção de editar anúncio sem alterações. |
| 4. O vendedor pode continuar alterando os outros campos do anúncio. | |

---

# UC020 - Alterar Localização

# Descrição

| Código / Nome do Caso de Uso | UC020 - Alterar Localização |
|-----------------------------|--------------------------------|
| **Ator Principal**          | Vendedor |
| **Resumo**                  | Neste caso de uso, o vendedor pode alterar a localização do veículo em um anúncio em edição. |
| **Pré-condições**           | O vendedor deve estar autenticado no sistema e o anúncio deve estar em processo de edição. |
| **Pós-condições**           | A localização do anúncio é atualizada. |

---

# Fluxo Principal

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O vendedor acessa a opção de editar o anúncio. | |
| | 2. O sistema exibe a localização atual do veículo. |
| 3. O vendedor insere a nova localização. | |
| | 4. O sistema valida os dados e armazena a informação. |
| | 5. O sistema confirma a atualização da localização. |

---

# Fluxo Alternativo 1 - Localização inválida

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| | 2. O sistema detecta que a localização inserida não é válida. |
| | 3. O sistema solicita uma nova localização. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 2 - Nenhuma localização adicionada

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor não adiciona uma localização. | |
| | 3. O sistema solicita uma localização. |
| 4. O vendedor pode tentar novamente. | |

---

# Fluxo Alternativo 3 - Não alterar localização

| **Usuário** | **Sistema** |
|---------------|-------------|
| 1. O fluxo segue até o passo 3. | |
| 2. O vendedor decide não modificar a localização. | |
| | 3. O sistema retorna à opção de editar anúncio sem alterações. |
| 4. O vendedor pode continuar alterando os outros campos do anúncio. | |

---