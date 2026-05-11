# Versão Corrigida e Refatorada com Tratamento de Erros

Aqui apresentamos uma versão aprimorada da função `processarVenda`, aplicando conceitos de programação defensiva, validação de regras de negócio e tratamento estruturado de exceções.

## Código Refatorado

```java
public Venda processarVenda(Veiculo veiculo, Cliente cliente, double descontoPercentual) {

    try {

        // 1.Validação de objetos obrigatórios
        if (veiculo == null) {
            throw new IllegalArgumentException("Erro: O veículo informado é nulo.");
        }

        if (cliente == null) {
            throw new IllegalArgumentException("Erro: O cliente informado é nulo.");
        }

        // 2.Validação do percentual de desconto
        if (descontoPercentual < 0 || descontoPercentual > 100) {
            throw new IllegalArgumentException("Erro: O desconto deve estar entre 0 e 100.");
        }

        // 3.Validação do status do veículo
        if (!"DISPONIVEL".equals(veiculo.getStatus())) {
            throw new IllegalStateException(
                "Erro: O veículo não está disponível para venda."
            );
        }

        // 4.Cálculo correto do desconto
        double valorDesconto =
                veiculo.getPreco() * (descontoPercentual / 100.0);

        double precoFinal =
                veiculo.getPreco() - valorDesconto;

        // 5.Garantia de valor final válido
        if (precoFinal <= 0) {
            throw new ArithmeticException(
                "Erro: O preço final da venda é inválido."
            );
        }

        // 6.Atualização do status do veículo
        veiculo.setStatus("VENDIDO");

        // 7.Persistência no banco
        veiculoRepository.save(veiculo);

        // 8.Retorno da venda concluída
        return new Venda(veiculo, cliente, precoFinal);

    } catch (IllegalArgumentException e) {

        System.out.println("Falha de validação de entrada: " + e.getMessage());
        throw e;

    } catch (IllegalStateException e) {

        System.out.println("Falha de regra de negócio: " + e.getMessage());
        throw e;

    } catch (ArithmeticException e) {

        System.out.println("Erro matemático no cálculo da venda: " + e.getMessage());
        throw e;

    } catch (Exception e) {

        System.out.println("Erro inesperado ao processar venda: " + e.getMessage());

        throw new RuntimeException(
            "Falha interna ao processar a venda.",
            e
        );
    }
}
```

---

# Melhorias Aplicadas

## Validação Defensiva de Entradas

O método agora verifica:

- Veículo nulo
- Cliente nulo
- Percentual de desconto inválido

Essas validações evitam erros de execução como `NullPointerException` e entradas inconsistentes.

---

## Tratamento de Regras de Negócio

Foi adicionada uma validação para impedir a venda de veículos que não estejam com status `"DISPONIVEL"`.

Isso evita:

- Dupla venda
- Venda de veículos em manutenção
- Inconsistência de estoque

---

## Correção Matemática

O cálculo do desconto foi separado em duas etapas:

```java
double valorDesconto = veiculo.getPreco() * (descontoPercentual / 100.0);
double precoFinal = veiculo.getPreco() - valorDesconto;
```

Isso melhora:

- Legibilidade
- Manutenção
- Confiabilidade do cálculo

---

## Estrutura de Try-Catch

Foram adicionados blocos `catch` específicos para diferentes tipos de erro:

| Tipo de Exceção | Finalidade |
|---|---|
| `IllegalArgumentException` | Erros de entrada |
| `IllegalStateException` | Violação de regra de negócio |
| `ArithmeticException` | Problemas matemáticos |
| `Exception` | Erros inesperados |

Isso torna o sistema:

- Mais seguro
- Mais previsível
- Mais fácil de depurar

---

## Tratamento Genérico de Falhas

O bloco:

```java
catch (Exception e)
```

garante que erros inesperados sejam tratados adequadamente, evitando o encerramento abrupto da aplicação.

---
