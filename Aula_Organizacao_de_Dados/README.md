# Atividade: Organização de Dados - Do Caos à Ordem

**Instituição:** UDF Centro Universitário
**Disciplina:** Pensamento Computacional
**Docente:** Prof.ª Valéria
**Aluno:** Guilherme Rodrigues de Almeida

---

## Contexto e Objetivos

Esta atividade foca no pilar de Organização de Dados do Pensamento Computacional. O objetivo fundamental é demonstrar a transição de dados brutos para estruturas organizadas que permitem a computação eficiente e a tomada de decisão.

Para o projeto **MCG Auto**, selecionamos o domínio do **Catálogo de Peças e Compatibilidade**. A gestão de peças num ambiente automóvel é um exemplo clássico de "caos" que exige múltiplas formas de organização:
1. **Linear:** Para inventário e contagem simples.
2. **Hierárquica:** Para navegação lógica por sistemas do veículo.
3. **Relacional (Grafo):** Para mapear quais peças servem em quais modelos de carros (compatibilidade cruzada).

---

## Estruturas de Dados Aplicadas

### 1. Representação Linear (Lista)
Utilizada para o inventário bruto do stock. É a forma mais simples de organização, onde cada item ocupa uma posição sequencial.
- **Ficheiro:** `Lista.md`

### 2. Representação em Níveis (Hierarquia)
Utilizada para classificar as peças dentro da anatomia do veículo (Ex: Motor -> Sistema de Arrefecimento -> Radiador).
- **Ficheiro:** `Hierarquia.png`

### 3. Representação em Rede (Grafo)
Utilizada para resolver o problema da compatibilidade. Um "nó" (peça) pode estar conectado a múltiplos "nós" (modelos de veículos), demonstrando relações que uma lista ou árvore não suportariam.
- **Ficheiro:** `Grafo.png`

---

## Estrutura do Repositório

De acordo com o protocolo de entrega da atividade "Organização de Dados", o repositório está organizado da seguinte forma:

```text
Aula_Organizacao_Dados_GrupoX/
│
├── README.md          # Explicação da atividade, contexto e objetivos do projeto MCG Auto
├── Lista.md           # Representação linear (Inventário de peças em stock)
├── Hierarquia.png     # Representação em níveis (Organograma técnico do veículo)
└── Grafo.png          # Representação em rede (Mapa de conexões e compatibilidade de peças)
