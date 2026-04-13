# UCP IA APLICADA A ENGENHARIA DE SOFTWARE
   
## Tarefa 1

## Tarefa 2

**O texto abaixo foi feito utilizando o modelo do code llama juntamente da chave API do Groq para informar possiveis erros e corrigir o seguinte codigo em java**

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

---

#### Codigo utilizado

```from groq import Groq

client = Groq(api_key="")

completion = client.chat.completions.create(
    model="llama-3.3-70b-versatile",
    messages=[
        {
            "role": "system",
            "content": "Você é um especialista em programação. Analise códigos e corrija possíveis erros."
        },
        {
            "role": "user",
            "content": "Analise o seguinte código Java e corrija possíveis problemas:\n\npublic int divide(int a, int b){ return a / b; }"
        }
    ],
    temperature=0.7,
    max_completion_tokens=1024,
    top_p=1,
    stream=True
)   

for chunk in completion:
    print(chunk.choices[0].delta.content or "", end="")
 ```
---

#### Possiveis erros

**O uso de doubles pode causar imprecisão**

Embora double resolva a divisão decimal, ele pode gerar erros de precisão:

0.1 + 0.2 != 0.3

**Possível overflow de inteiros**

Existe um caso especifico em que ele pode gerar overflow

Integer.MIN_VALUE / -1

Esse cálculo resulta em um valor fora do limite do tipo int.

### Segunda etapa da tarefa

**O  resultado seguinte foi gerado pelo codeLLama , utilizando o mesmo código anterior e mudando apenas o prompt**

**Análise do Código**

O código fornecido é um método Java que realiza a divisão de dois números inteiros. No entanto, há um problema potencial com este código: ele não lida com a possibilidade de divisão por zero.

**Correção do Código**

Aqui está a versão corrigida do código:
```java
/**
 * Realiza a divisão de dois números inteiros.
 * 
 * @param a o dividendo
 * @param b o divisor
 * @return o resultado da divisão
 * @throws ArithmeticException se o divisor for zero
 */
public int divide(int a, int b) {
    if (b == 0) {
        throw new ArithmeticException("Divisão por zero");
    }
    return a / b;
}
```
**Testes Automatizados**

Aqui estão alguns testes automatizados para o método `divide` usando JUnit:
```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertThrows;

public class DivideTest {
    @Test
    public void testDivideValido() {
        assertEquals(2, divide(4, 2));
        assertEquals(-2, divide(4, -2));
        assertEquals(-2, divide(-4, 2));
        assertEquals(2, divide(-4, -2));
    }

    @Test
    public void testDividePorZero() {
        assertThrows(ArithmeticException.class, () -> divide(4, 0));
    }
}
```
**Documentação**

A documentação para o método `divide` foi adicionada como um comentário Javadoc. Isso fornece uma descrição clara do que o método faz, dos parâmetros que aceita e do valor que retorna.

**Mensagem de Commit**

Aqui está uma mensagem de commit apropriada para as alterações feitas:
```
Correção do método divide para lidar com divisão por zero

* Adicionado tratamento de exceção para divisão por zero
* Adicionados testes automatizados para validar o comportamento do método
```
**Problemas Corrigidos**

Os problemas corrigidos incluem:

* Divisão por zero: o método agora lida com essa situação e lança uma exceção `ArithmeticException` apropriada.
* Falta de documentação: a documentação foi adicionada para fornecer uma descrição clara do que o método faz.
* Falta de testes: os testes automatizados foram adicionados para validar o comportamento do método.

---

### Codigo utilizado

```
from groq import Groq

client = Groq(api_key="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")

completion = client.chat.completions.create(
    model="llama-3.3-70b-versatile",
    messages=[
        {
            "role": "system",
            "content": "Você é um especialista em programação. Analise códigos e corrija possíveis erros."
        },
        {
            "role": "user",
            "content": "Analise o seguinte código Java e gere testes automatizados , documentação e mensagem de commit , também corrija possiveis problemas:\n\npublic int divide(int a, int b){ return a / b; }"
        }
    ],
    temperature=0.7,
    max_completion_tokens=1024,
    top_p=1,
    stream=True
)   

for chunk in completion:
    print(chunk.choices[0].delta.content or "", end="")
```

---








