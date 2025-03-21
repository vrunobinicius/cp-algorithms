# ⚡ Explicação do Algoritmo de Exponenciação Rápida ⚡

## 🚀 Introdução
O algoritmo apresentado implementa a **exponenciação rápida** (também conhecida como *binary exponentiation*), uma técnica eficiente para calcular potências de um número de forma recursiva ou iterativa.

## 💻 Código-fonte (Recursivo)

```cpp
#include <bits/stdc++.h>

using namespace std;

long long binpow(int a, int b)
{
    if (b == 0)
        return 1;

    long long res = binpow(a, b / 2);

    if (b % 2)
        return res * res * a;
    else
        return res * res;
}

int main(int argc, char const *argv[])
{
    long long a, b;

    cin >> a >> b;

    cout << binpow(a, b) << "\n";

    return 0;
}
```

## 💻 Código-fonte (Iterativo)

```cpp
#include <bits/stdc++.h>

using namespace std;

long long binpow(long long a, long long b)
{
    long long res = 1;

    while (b > 0)
    {
        if (b & 1)
            res *= a;
        a *= a;
        b >>= 1;
    }
    return res;
}

int main(int argc, char const *argv[])
{
    long long a, b;

    cin >> a >> b;

    cout << binpow(a, b) << "\n";

    return 0;
}
```

## 📖 Explicação do Algoritmo

### 1. **Função `binpow` (Recursiva) 🧮**
A função `binpow(int a, int b)` implementa a exponenciação rápida de forma recursiva:

- **🔹 Caso base:** Se `b == 0`, o resultado é `1`, pois qualquer número elevado a `0` é `1`.
- **🔹 Divisão do problema:** O algoritmo divide a potência em subproblemas menores, reduzindo `b` pela metade a cada chamada recursiva.
- **🔹 Cálculo do resultado:**
  - Se `b` é **par**, então `a^b = (a^(b/2))^2`.
  - Se `b` é **ímpar**, então `a^b = (a^(b/2))^2 * a`.

### 2. **Função `binpow` (Iterativa) 🔄**
A versão iterativa da função `binpow(long long a, long long b)` usa um loop `while` para calcular a potência:

- **🔹 Inicialização:** `res = 1` para armazenar o resultado.
- **🔹 Loop de Exponenciação:**
  - Se `b` for ímpar (`b & 1`), multiplica `res` por `a`.
  - Atualiza `a` elevando-o ao quadrado.
  - Reduz `b` pela metade usando `b >>= 1` (bitwise shift para a direita).
- **🔹 Retorno:** O resultado final é armazenado em `res`.

### 3. **Função `main`** 🎯
- 📥 Lê dois valores `a` e `b` da entrada padrão.
- 🔢 Calcula `a^b` chamando `binpow(a, b)`.
- 📤 Imprime o resultado na saída padrão.

## ⏳ Complexidade do Algoritmo
A complexidade da exponenciação rápida, tanto recursiva quanto iterativa, é **O(log b)**, pois o valor de `b` é reduzido pela metade a cada iteração ou chamada recursiva. Isso torna o algoritmo muito mais eficiente do que uma abordagem ingênua de multiplicação repetida (**O(b)**).

## 📝 Exemplo de Execução
### 📌 Entrada:
```
3 10
```
### ⚙️ Processamento:
O algoritmo calcula:
```
3^10 = ((3^5)^2)
       = (((3^2)^2 * 3)^2)
       = (((9)^2 * 3)^2)
       = ((81 * 3)^2)
       = (243^2)
       = 59049
```
### 📌 Saída:
```
59049
```

## 🎯 Conclusão
A técnica de **exponenciação rápida** é amplamente utilizada em computação, especialmente em problemas que envolvem grandes exponenciações, como criptografia 🔐, computação modular e algoritmos matemáticos otimizados. A versão iterativa tende a ser mais eficiente em termos de memória, pois evita chamadas recursivas.

