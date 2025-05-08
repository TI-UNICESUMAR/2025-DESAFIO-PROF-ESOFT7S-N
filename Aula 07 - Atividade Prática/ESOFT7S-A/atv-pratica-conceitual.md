# Plano de Gerenciamento de Software: Problemática (Realização em aula: 09/05)

## Contexto

Você gerencia um sistema de centralização de vendas de produtos, semelhante ao Mercado Livre, que conecta vendedores, compradores e entregadores. O sistema está em operação com as seguintes características:

- **Base de Usuários Atual**:
  - 50 vendedores
  - 50 entregadores
  - 100 compradores
  - Total: **200 usuários**
- **Funcionalidades Principais**:
  - **Compras Online**: Interface para compradores navegarem, selecionarem e comprarem produtos.
  - **Dash dos Vendedores**: Painel para vendedores gerenciarem produtos, estoques e pedidos.
  - **Entregas**: Sistema para entregadores visualizarem e gerenciarem entregas.
- **Arquitetura Atual**:
  - **Microserviços**: Cada frente (Compras Online, Dash Vendedores, Entregas) possui sua própria API.
  - **Banco de Dados**: Um único banco de dados centralizado é compartilhado por todas as APIs.
  - **Taxa de Requisições**: Média de **10 requisições por minuto**.
- **Diagrama do Ambiente Atual**:
  ```
  [Compradores] --> [API Compras Online] --\
                                            \
  [Vendedores] --> [API Dash Vendedores] --> [Banco de Dados Central]
                                            /
  [Entregadores] --> [API Entregas] ------/
  ```
  - **Descrição**: Cada API (Compras, Vendedores, Entregas) recebe requisições dos respectivos usuários e interage com o mesmo banco de dados relacional. As APIs são independentes, mas o banco centralizado é o ponto de convergência.

## Problemática

Recentemente, a base de usuários cresceu de **200 para 100.000 usuários**, resultando em sobrecarga no sistema e os seguintes problemas:

1. **Vendas de Produtos sem Estoque**:
   - Múltiplos pedidos simultâneos para o mesmo produto causaram vendas de itens que já estavam esgotados, devido a falhas na sincronização ou validação de estoque.
2. **Lentidão nas Requisições**:
   - O banco de dados não consegue processar atualizações de estoque e retornar listas de produtos em tempo hábil, causando atrasos perceptíveis.
3. **Quedas Frequentes da Aplicação**:
   - O aumento na taxa de requisições, de **10 para 1.000 requisições por minuto**, sobrecarrega o sistema, levando a instabilidades e quedas.

## Perguntas

1. Quais são as soluções arquiteturais possíveis para resolver esses problemas?
2. Quais ferramentas podem auxiliar na implementação dessas soluções?
3. Ajuste o Diagrama do Ambiente Atual para a solução aplicada.

## Link da Resposta

Apresente a solução em um documento básico. (PDF/DOCS)

[Forms](https://forms.gle/t1r2XaKrSeF7z3XCA)
