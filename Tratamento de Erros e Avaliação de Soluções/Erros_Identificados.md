# Registro de Erros Identificados no Algoritmo Original

Abaixo está a versão inicial da função `processarVenda` (camada Service do backend), contendo falhas críticas antes da refatoração.

## Código Original (Com Erros)

```java
public Venda processarVenda(Veiculo veiculo, Cliente cliente, double descontoPercentual) {
    // Processamento da venda
    
    // Calcula o preço com desconto
    double precoFinal = veiculo.getPreco() - descontoPercentual / 100; 

    // Altera o status e salva
    veiculo.setStatus("VENDIDO");
    veiculoRepository.save(veiculo);
    
    return new Venda(veiculo, cliente, precoFinal);
}
```

---

# Mapeamento dos Bugs

## Erro de Ação Defensiva (Risco de Execução)

### Descrição
O sistema não verifica se os objetos `veiculo` ou `cliente` são nulos antes de tentar acessar seus métodos (ex: `veiculo.getPreco()`).

### Consequência
Risco iminente de um `NullPointerException`, causando o travamento do sistema.

---

## Erro Lógico por Ambiguidade (Conflito de Regras)

### Descrição
A função não valida o status atual do veículo antes de vendê-lo.

### Consequência
Um carro que já possui o status `"VENDIDO"` ou `"EM MANUTENÇÃO"` pode ser vendido novamente para outro cliente (dupla venda).

---

## Erro Lógico-Matemático (Falha de Prioridade Operacional)

### Descrição
Erro de parênteses na fórmula matemática de desconto. O valor de `descontoPercentual / 100` é calculado primeiro e subtraído do preço total, em vez de se calcular a porcentagem sobre o preço.

### Consequência
Se um carro custa `R$ 50.000,00` e o desconto for de `10%`, a conta fará:

```java
50000 - (10 / 100)
```

Resultando no preço de:

```text
R$ 49.999,90
```

O que é financeiramente incorreto.

---
