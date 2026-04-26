# Desafios Identificados e Mitigação: MCG Auto

Este documento descreve os desafios críticos previstos para o sistema MCG Auto e as estratégias de engenharia para mitigar riscos de escalabilidade e segurança.

## 1. Dificuldades Essenciais (O Domínio)
* **Complexidade e Mutabilidade:** O software deve adaptar-se a mudanças constantes em regras fiscais e políticas de preços das montadoras.
* **Mitigação:** Arquitetura baseada em microsserviços, permitindo que o módulo de vendas seja atualizado sem afetar o inventário global.

## 2. Escalabilidade e Tolerância a Falhas
* **Desafio:** Gestão de milhares de pedidos simultâneos e manutenção da consistência de dados entre filiais geograficamente distantes.
* **Mitigação:** Utilização de redundância de servidores e sistemas de cache para leitura rápida de inventário. O algoritmo de "Locking" garante a integridade dos dados mesmo sob alta carga.

## 3. Segurança da Informação (Saltzer & Schroeder)
* **Desafio:** Proteção contra acessos não autorizados a dados financeiros e informações sensíveis de clientes.
* **Mitigação (Menor Privilégio):** Vendedores acedem apenas aos dados da sua própria filial; apenas a direção tem acesso aos relatórios globais.
* **Mitigação (Bloqueio por Padrão):** Por defeito, qualquer novo utilizador ou recurso tem o acesso negado, sendo necessária uma concessão explícita de privilégios.
* **Mitigação (Separação de Privilégios):** Operações críticas, como grandes descontos ou estornos, exigem a aprovação dupla (Vendedor + Gerente).

## 4. Dificuldades Acidentais: Integrações
* **Desafio:** Dependência de APIs externas de terceiros (financeiras e órgãos de trânsito) que podem sofrer alterações ou indisponibilidade.
* **Mitigação:** Camada de abstração (Gateway) para isolar as integrações. Caso uma API externa mude, apenas o adaptador correspondente precisa de ser atualizado, mantendo o núcleo do MCG Auto intacto.