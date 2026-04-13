# UCP IA APLICADA A ENGENHARIA DE SOFTWARE
   
## Tarefa 1

## Tarefa 2
```java
public int divide(int a, int b) {
    if (b == 0) {
        throw new ArithmeticException("Divisão por zero não é permitida");
    }
    return a / b;
}
```

Nessa versão corrigida, adicionamos uma verificação para garantir que o denominador não seja zero antes de realizar a divisão. Se `b` for zero, lançamos uma exceção `ArithmeticException` com uma mensagem clara indicando o problema.

No entanto, é importante notar que essa abordagem ainda não lida com o problema da perda de precisão devido à divisão de números inteiros. Se você precisar realizar divisões com números decimais, considere usar o tipo `double` em vez de `int`:

```java
public double divide(double a, double b) {
    if (b == 0) {
        throw new ArithmeticException("Divisão por zero não é permitida");
    }
    return a / b;
}
```







