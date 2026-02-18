# Documento de Casos de Testes - Sistema McBugs

**Sistema:** McBugs - Totem de Autoatendimento  
**Data de Criação:** 2025-01-27  
**Versão:** 1.0  
**Objetivo:** Casos de teste funcionais a nível de jornada para os fluxos "Para comer aqui" e "Para levar"

---

## CT001 - Jornada Completa: Pedido "Para Comer Aqui"

#### **Objetivo**

Validar o fluxo completo de realização de um pedido do tipo "Para comer aqui" (dine-in), desde a seleção do tipo de pedido na página inicial até a confirmação final do pagamento, garantindo que todos os passos funcionem corretamente e que o pedido seja registrado adequadamente no sistema.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- A conexão com a internet deve estar ativa.
- O banco de dados Supabase deve estar configurado e funcionando.
- O sistema deve estar sem itens no carrinho (carrinho vazio).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a URL raiz do sistema (/) | A página inicial deve ser carregada corretamente, exibindo o logo do McBugs, a mensagem "Seja bem-vindo!" e as duas opções de pedido. |
| 2      | Clicar no botão "Para comer aqui" | O sistema deve definir o tipo de pedido como "dine-in" e redirecionar automaticamente para a página /menu. |
| 3      | Verificar a página do menu         | A página do menu deve ser exibida com as categorias de produtos (Lanches, Fritas, Bebidas, Sobremesas) e os produtos disponíveis. |
| 4      | Selecionar uma categoria (ex: Lanches) | Os produtos da categoria selecionada devem ser exibidos em formato de grid. |
| 5      | Clicar em um produto do cardápio   | O sistema deve redirecionar para a página de detalhes do produto (/product/{id}). |
| 6      | Verificar os detalhes do produto   | A página deve exibir a imagem do produto, nome, preço, descrição, ingredientes (se houver) e controle de quantidade. |
| 7      | Ajustar a quantidade desejada (ex: 2 unidades) | O controle de quantidade deve permitir aumentar/diminuir e o preço total deve ser atualizado dinamicamente. |
| 8      | Clicar no botão "Quero • {preço}"  | O produto deve ser adicionado ao carrinho com a quantidade especificada e o sistema deve redirecionar para /menu. |
| 9      | Verificar o indicador de itens no carrinho | O ícone de carrinho deve exibir o número total de itens adicionados. |
| 10     | Adicionar mais produtos ao carrinho (repetir passos 5-8) | Os produtos adicionais devem ser incluídos no carrinho e o contador deve ser atualizado. |
| 11     | Clicar no ícone do carrinho ou no botão "Ver pedido" | O sistema deve redirecionar para a página /cart exibindo todos os itens adicionados. |
| 12     | Verificar os itens no carrinho     | Todos os produtos adicionados devem ser exibidos com suas respectivas quantidades e preços individuais. |
| 13     | Ajustar a quantidade de um item no carrinho | O sistema deve permitir aumentar ou diminuir a quantidade e atualizar o preço total automaticamente. |
| 14     | Remover um item do carrinho (se necessário) | O item deve ser removido do carrinho e o total deve ser recalculado. |
| 15     | Verificar o total do pedido        | O total do pedido deve estar correto, somando todos os itens com suas quantidades. |
| 16     | Clicar no botão "Finalizar pedido" | Um drawer deve ser aberto solicitando o nome do cliente. |
| 17     | Inserir o nome do cliente no campo "Seu nome" | O campo deve aceitar a entrada de texto. |
| 18     | Clicar no botão "Finalizar" no drawer | O sistema deve criar o pedido no banco de dados, exibir mensagem de carregamento "enviando a cozinha...." e redirecionar para /payment. |
| 19     | Verificar a página de pagamento   | A página deve exibir o resumo do pedido (número do pedido, total) e as opções de pagamento (PIX, Cartão de Débito, Cartão de Crédito). |
| 20     | Verificar que o tipo de pedido está como "Comer no local" | O tipo de pedido "dine-in" deve estar registrado corretamente. |
| 21     | Selecionar um método de pagamento (ex: PIX) | O sistema deve atualizar o método de pagamento do pedido e redirecionar para a página de confirmação correspondente. |
| 22     | Verificar a página de confirmação de pagamento | A página deve exibir: número do pedido, total, detalhes do cliente, tipo de pedido, método de pagamento, data/hora e lista de itens. |
| 23     | Verificar mensagem específica para "Para comer aqui" | Deve ser exibida uma mensagem informando: "Após o pagamento, aguarde ser chamado pelo número do seu pedido." |
| 24     | Clicar no botão "Fazer Novo Pedido" | O sistema deve limpar o carrinho, resetar o tipo de pedido e redirecionar para a página inicial (/). |

#### **Resultados Esperados**

- O tipo de pedido "dine-in" é selecionado e persistido corretamente.
- Os produtos são adicionados ao carrinho com sucesso.
- O carrinho mantém os itens e permite edição de quantidades.
- O pedido é criado no banco de dados com status "pending".
- O método de pagamento é atualizado corretamente.
- A confirmação exibe todas as informações do pedido corretamente.
- A mensagem específica para "Para comer aqui" é exibida na confirmação.
- O sistema permite iniciar um novo pedido após a conclusão.

#### **Critérios de Aceitação**

- Todos os passos são executados sem erros.
- O pedido é registrado no banco de dados Supabase com todos os campos corretos.
- O tipo de pedido "dine-in" é mantido em todo o fluxo.
- O total do pedido é calculado corretamente.
- A navegação entre as páginas ocorre sem problemas.
- A mensagem específica para pedidos "Para comer aqui" é exibida na confirmação.
- Não há erros no console do navegador.
- Os dados são persistidos corretamente no localStorage durante o fluxo.

---

## CT002 - Jornada Completa: Pedido "Para Levar"

#### **Objetivo**

Validar o fluxo completo de realização de um pedido do tipo "Para levar" (takeaway), desde a seleção do tipo de pedido na página inicial até a confirmação final do pagamento, garantindo que todos os passos funcionem corretamente e que o pedido seja registrado adequadamente no sistema.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- A conexão com a internet deve estar ativa.
- O banco de dados Supabase deve estar configurado e funcionando.
- O sistema deve estar sem itens no carrinho (carrinho vazio).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a URL raiz do sistema (/) | A página inicial deve ser carregada corretamente, exibindo o logo do McBugs, a mensagem "Seja bem-vindo!" e as duas opções de pedido. |
| 2      | Clicar no botão "Para levar"      | O sistema deve definir o tipo de pedido como "takeaway" e redirecionar automaticamente para a página /menu. |
| 3      | Verificar a página do menu         | A página do menu deve ser exibida com as categorias de produtos (Lanches, Fritas, Bebidas, Sobremesas) e os produtos disponíveis. |
| 4      | Selecionar uma categoria (ex: Bebidas) | Os produtos da categoria selecionada devem ser exibidos em formato de grid. |
| 5      | Clicar em um produto do cardápio   | O sistema deve redirecionar para a página de detalhes do produto (/product/{id}). |
| 6      | Verificar os detalhes do produto   | A página deve exibir a imagem do produto, nome, preço, descrição, ingredientes (se houver) e controle de quantidade. |
| 7      | Ajustar a quantidade desejada (ex: 1 unidade) | O controle de quantidade deve permitir aumentar/diminuir e o preço total deve ser atualizado dinamicamente. |
| 8      | Clicar no botão "Quero • {preço}"  | O produto deve ser adicionado ao carrinho com a quantidade especificada e o sistema deve redirecionar para /menu. |
| 9      | Verificar o indicador de itens no carrinho | O ícone de carrinho deve exibir o número total de itens adicionados. |
| 10     | Adicionar mais produtos ao carrinho (repetir passos 5-8) | Os produtos adicionais devem ser incluídos no carrinho e o contador deve ser atualizado. |
| 11     | Clicar no ícone do carrinho ou no botão "Ver pedido" | O sistema deve redirecionar para a página /cart exibindo todos os itens adicionados. |
| 12     | Verificar os itens no carrinho     | Todos os produtos adicionados devem ser exibidos com suas respectivas quantidades e preços individuais. |
| 13     | Ajustar a quantidade de um item no carrinho | O sistema deve permitir aumentar ou diminuir a quantidade e atualizar o preço total automaticamente. |
| 14     | Remover um item do carrinho (se necessário) | O item deve ser removido do carrinho e o total deve ser recalculado. |
| 15     | Verificar o total do pedido        | O total do pedido deve estar correto, somando todos os itens com suas quantidades. |
| 16     | Clicar no botão "Finalizar pedido" | Um drawer deve ser aberto solicitando o nome do cliente. |
| 17     | Inserir o nome do cliente no campo "Seu nome" | O campo deve aceitar a entrada de texto. |
| 18     | Clicar no botão "Finalizar" no drawer | O sistema deve criar o pedido no banco de dados, exibir mensagem de carregamento "enviando a cozinha...." e redirecionar para /payment. |
| 19     | Verificar a página de pagamento   | A página deve exibir o resumo do pedido (número do pedido, total) e as opções de pagamento (PIX, Cartão de Débito, Cartão de Crédito). |
| 20     | Verificar que o tipo de pedido está como "Para levar" | O tipo de pedido "takeaway" deve estar registrado corretamente. |
| 21     | Selecionar um método de pagamento (ex: Cartão de Crédito) | O sistema deve atualizar o método de pagamento do pedido e redirecionar para a página de confirmação correspondente. |
| 22     | Verificar a página de confirmação de pagamento | A página deve exibir: número do pedido, total, detalhes do cliente, tipo de pedido, método de pagamento, data/hora e lista de itens. |
| 23     | Verificar que não há mensagem específica para "Para levar" | Não deve ser exibida a mensagem "Após o pagamento, aguarde ser chamado pelo número do seu pedido." (essa mensagem é apenas para dine-in). |
| 24     | Clicar no botão "Fazer Novo Pedido" | O sistema deve limpar o carrinho, resetar o tipo de pedido e redirecionar para a página inicial (/). |

#### **Resultados Esperados**

- O tipo de pedido "takeaway" é selecionado e persistido corretamente.
- Os produtos são adicionados ao carrinho com sucesso.
- O carrinho mantém os itens e permite edição de quantidades.
- O pedido é criado no banco de dados com status "pending".
- O método de pagamento é atualizado corretamente.
- A confirmação exibe todas as informações do pedido corretamente.
- A mensagem específica para "Para comer aqui" NÃO é exibida na confirmação (pois é takeaway).
- O sistema permite iniciar um novo pedido após a conclusão.

#### **Critérios de Aceitação**

- Todos os passos são executados sem erros.
- O pedido é registrado no banco de dados Supabase com todos os campos corretos.
- O tipo de pedido "takeaway" é mantido em todo o fluxo.
- O total do pedido é calculado corretamente.
- A navegação entre as páginas ocorre sem problemas.
- A mensagem específica para pedidos "Para comer aqui" NÃO é exibida na confirmação (diferenciação correta entre os tipos).
- Não há erros no console do navegador.
- Os dados são persistidos corretamente no localStorage durante o fluxo.

---

## Observações Gerais

### Diferenças entre os Fluxos

- **Para Comer Aqui (dine-in):** Exibe mensagem informando que o cliente deve aguardar ser chamado pelo número do pedido após o pagamento.
- **Para Levar (takeaway):** Não exibe a mensagem de aguardo, pois o cliente retira o pedido no balcão.

### Métodos de Pagamento Disponíveis

- **PIX:** Pagamento via código PIX (simulado com confirmação automática após 5 segundos)
- **Cartão de Débito:** Pagamento no balcão na hora da retirada
- **Cartão de Crédito:** Pagamento no balcão na hora da retirada

### Persistência de Dados

- O tipo de pedido é salvo no localStorage com a chave `mcbugs-order-type`.
- Os itens do carrinho são salvos no localStorage com a chave `mcbugs-cart-items`.
- O pedido atual é salvo no localStorage com a chave `mcbugs-current-order`.

### Estados do Pedido

- **pending:** Pedido criado, aguardando pagamento
- **paid:** Pagamento confirmado
- **preparing:** Pedido sendo preparado
- **ready:** Pedido pronto para retirada
- **completed:** Pedido concluído
- **cancelled:** Pedido cancelado

---

**Fim do Documento**

