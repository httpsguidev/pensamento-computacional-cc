# Design do Sistema: MCG Auto

Este documento detalha a aplicação dos pilares do Pensamento Computacional no design da arquitetura do MCG Auto, garantindo que o sistema seja modular, escalável e seguro para uma operação em larga escala.

## 1. Decomposição (Motor Mental)
A decomposição consiste em dividir o sistema em módulos ou microsserviços gerenciáveis para reduzir a complexidade técnica. O MCG Auto foi estruturado nos seguintes componentes:

* **Serviço de Inventário Global:** Gere o estado unificado dos veículos (marca, modelo, chassi e localização) em tempo real para todas as filiais da rede.
* **Serviço de Vendas (Transacional):** Responsável pelo fluxo de fecho de contratos, cálculo automático de comissões e integração com gateways de pagamento.
* **Serviço de Identidade (IAM):** Centraliza a autenticação e aplica regras de acesso estritas baseadas no cargo e na unidade física do colaborador.
* **Serviço de Auditoria e Segurança:** Monitoriza logs de transações e executa varreduras automáticas de vulnerabilidades na infraestrutura.

## 2. Abstração e Reconhecimento de Padrões
A abstração permite focar na essência funcional, enquanto os padrões identificam soluções já validadas em sistemas de alta complexidade.

* **Padrão de Reserva (Locking):** Implementação de um padrão de concorrência inspirado em sistemas de e-commerce globais. Quando um veículo é selecionado para venda, o chassi é bloqueado temporariamente para evitar vendas duplicadas por diferentes filiais.
* **Modelo Abstrato de Veículo:** O sistema interage com uma entidade simplificada (ID_Chassi, Status, Preço) nos fluxos críticos, carregando detalhes estéticos apenas quando necessário para otimizar o processamento.
* **Interface Consistente:** Utilização de padrões de UI/UX comuns em sistemas ERP para reduzir a carga cognitiva dos utilizadores e acelerar a aprendizagem.

## 3. Algoritmos
Mapeamento dos fluxos críticos para garantir a precisão e a eficiência na execução das tarefas automatizadas.

### Fluxo de Validação de Disponibilidade
1. **Entrada:** Recebe o `ID_Chassi` e o `ID_Vendedor`.
2. **Processamento:**
   - **Se** o status do veículo for "Disponível", **então** altera para "Reserva_Temporária" (bloqueio de 15 min).
   - **Senão**, nega a operação e exibe a mensagem "Item em Negociação".
3. **Saída:** Retorna a permissão para o checkout ou o erro de bloqueio.

## 4. Segurança Integrada (Saltzer & Schroeder)
* **Menor Privilégio:** Cada utilizador tem permissões limitadas à sua função específica.
* **Mediação Completa:** Todas as solicitações ao banco de dados são verificadas pelo serviço de identidade antes da execução.