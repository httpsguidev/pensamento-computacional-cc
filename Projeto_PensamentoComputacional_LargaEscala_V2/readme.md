# Pensamento Computacional: A Arte da Abstração

**Instituição:** UDF Centro Universitário
**Disciplina:** Pensamento Computacional
**Docente:** Prof.ª Valéria
**Aluno:** Guilherme Rodrigues de Almeida

---

## Contexto e Objetivos

Este repositório contém a entrega da "Missão Prática: Do mundo real ao pseudocódigo". O objetivo central desta atividade é exercitar o motor do pensamento computacional através da **Abstração** e **Decomposição**. 

A tarefa consiste em selecionar uma situação quotidiana complexa e aparentemente caótica, filtrando-a através de um processo de redução de complexidade para focar apenas no essencial para a resolução do problema. A transição ocorre em três níveis evolutivos: desde a descrição exaustiva humana até à lógica estruturada computacional.

---

## Situação Escolhida: Agendamento de Manutenção Automóvel

A situação do mundo real escolhida foi o processo de **Agendar a Manutenção de um Veículo numa Concessionária/Oficina**. No mundo real, este processo envolve interações humanas, conversas paralelas, verificação de agendas físicas ou sistemas lentos, e a procura por um mecânico que saiba resolver o problema específico do carro.

Abaixo, demonstramos como esse caos é simplificado.

### Nível 1: Descrição Detalhada (O processo bruto)
*(O passo a passo exaustivo do utilizador, sem filtros)*

1. O cliente pega no telemóvel e desbloqueia o ecrã.
2. Abre a aplicação de mensagens e envia um "Bom dia" para a oficina.
3. Aguarda 10 minutos pela resposta do assistente.
4. O cliente explica que o carro está a fazer um barulho estranho na roda direita há 3 dias.
5. O assistente pede o CPF do cliente para o encontrar no sistema.
6. O cliente vai até à carteira, tira o documento e digita o CPF.
7. O assistente pergunta qual a matrícula do veículo e qual o serviço que deseja (ex: Revisão, Suspensão).
8. O cliente informa a matrícula e diz que precisa de verificar a suspensão na próxima sexta-feira.
9. O assistente olha para a tabela de horários de todos os mecânicos, à procura de um especialista em suspensão que tenha a sexta-feira livre.
10. O assistente encontra o mecânico "João" livre na sexta-feira.
11. O assistente cria a Ordem de Serviço, anota todos os dados e avisa o cliente que está confirmado.
12. O cliente agradece e bloqueia o telemóvel.

### Nível 2: Representação Intermediária (O fluxo lógico)
*(Diagrama simplificado mostrando apenas as etapas principais, detalhes supérfluos removidos)*

O mapeamento lógico desta operação foi desenhado removendo as interações humanas irrelevantes e focando no fluxo de decisão. 

> **Acesso ao diagrama visual:** Ficheiro Fluxograma.png disponível neste repositório.

### Nível 3: Abstração Computacional (O algoritmo genérico)
*(Algoritmo que representa o processo de forma genérica e universal)*

A destilação final do problema. Aqui, a linguagem natural é substituída por variáveis, funções de busca e estruturas condicionais puras (Lógica de Médio/Alto Nível).

> **Acesso ao código estruturado:** Ficheiro Pseudocodigo.md disponível neste repositório.

---

## Estrutura do Repositório

- `README.md`: Explicação da atividade, contexto e detalhamento do Nível 1.
- `Fluxograma.png`: Representação intermediária e visual do Nível 2.
- `Pseudocodigo.md`: Representação algorítmica final do Nível 3.
