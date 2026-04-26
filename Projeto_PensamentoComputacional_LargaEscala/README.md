# Projeto – Pensamento Computacional para Sistemas de Larga Escala

## Descrição
Este projeto foi desenvolvido como parte da disciplina Pensamento Computacional no curso de Ciência da Computação.
O objetivo é aplicar os conceitos de pensamento computacional e engenharia de software na concepção de um sistema de larga escala, explorando decomposição, abstração, reconhecimento de padrões e algoritmos.

## Objetivos
* Relacionar engenharia de software e pensamento computacional.
* Reconhecer princípios e padrões relevantes para sistemas de larga escala.
* Identificar dificuldades reais no desenvolvimento de aplicações complexas.
* Aplicar metodologias ágeis no planejamento do projeto.

## Sistema Proposto
**Nome do Sistema:** MCG Auto - Gestão de Concessionárias em Rede
**Descrição:**
Uma aplicação web para gestão automotiva distribuída que integra:
* Cadastro e autenticação de funcionários e acessos filiais.
* Módulo de inventário global de veículos em tempo real.
* Sistema de processamento de vendas com prevenção de duplicidade.
* Painel de relatórios de desempenho para a diretoria.

## Pensamento Computacional Aplicado
**Decomposição:**
* Autenticação e Autorização 
* Gestão de Inventário Global
* Relatórios e Auditoria
* Processamento de Vendas

**Reconhecimento de Padrões:**
* Login com controle de permissões baseado no Princípio do Menor Privilégio.
* Estrutura de bloqueio e reserva inspirada em sistemas de e-commerce de alto tráfego.

**Abstração:**
* Diagrama simplificado em UML para representar a comunicação entre os módulos de estoque e transações.

**Algoritmos:**
* Fluxo de cálculo de comissões e validação condicional para evitar a dupla venda do mesmo chassi.

## Metodologia de Desenvolvimento
* **Metodologia:** Scrum
* **Sprints:** 2 semanas
* **Ferramentas:** GitHub Projects, Issues, Kanban

## Desafios Identificados
* Escalabilidade para múltiplas filiais acessando o mesmo banco de dados simultaneamente.
* Segurança de dados sensíveis e transações financeiras (princípios de Saltzer & Schroeder).
* Integração com sistemas externos (APIs de financeiras e órgãos de trânsito).

## 📂 Estrutura do Repositório
```text
Projeto_PensamentoComputacional_LargaEscala/
│
├── README.md              # Documentação principal 
├── Design.md              # Decomposição, abstração e padrões aplicados 
├── Diagrama.png           # Diagrama UML ou fluxograma 
├── Desafios.md            # Lista de desafios e soluções propostas 
└── src/                   # (Opcional) Protótipo ou código inicial