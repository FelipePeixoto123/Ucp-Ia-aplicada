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

**Codigo utilizado**

```from groq import Groq

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
            "content": "Analise o seguinte código Java e corrija possíveis problemas:\n\npublic int divide(int a, int b){ return a / b; }"
        }
    ],
    temperature=0.7,
    max_completion_tokens=1024,
    top_p=1,
    stream=True
)   

for chunk in completion:
    print(chunk.choices[0].delta.content or "", end="")```
 
---

###Possiveis erros

**O uso de doubles pode causar imprecisão**

Embora double resolva a divisão decimal, ele pode gerar erros de precisão:

0.1 + 0.2 != 0.3

**Possível overflow de inteiros**

Existe um caso especifico em que ele pode gerar overflow

Integer.MIN_VALUE / -1

Esse cálculo resulta em um valor fora do limite do tipo int.









