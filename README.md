[README.md](https://github.com/user-attachments/files/23126601/README.md)




# 🚀 Calculadora Científica em C (CLI - v2.0)

[![Licença](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Linguagem](https://img.shields.io/badge/Linguagem-C-informational.svg)]()
[![Status](https://img.shields.io/badge/Status-Funcional-success.svg)]()

Uma implementação robusta de uma calculadora científica em linguagem C, projetada para ser executada via linha de comando (CLI). O projeto demonstra conceitos de programação estruturada, modularidade de código, manipulação de estruturas (`struct`), alocação estática e, crucialmente, a implementação de um **Histórico de Operações Circular (FIFO)**.

---

## ✨ Funcionalidades

O programa oferece um total de 13 operações implementadas, além das funcionalidades de histórico e I/O robusto.

| Categoria | Opção | Descrição | Status |
| :--- | :--- | :--- | :---: |
| **Básicas** | 1-4 | Adição, Subtração, Multiplicação, Divisão (com validação de zero). | ✅ |
| **Potência** | 5 | Potência (`x^y`). | ✅ |
| **Radicais** | 6 | Raiz Quadrada (`sqrt`). | ✅ |
| **Especiais** | 7 | Fatorial (`x!`), com limite de 20 para `long double`. | ✅ |
| **Logaritmos** | 8 | Logaritmo Natural (`ln`). | ✅ |
| **Trigonometria**| 9-10 | Seno (`sin`) e Cosseno (`cos`), com entrada em Graus. | ✅ |
| **Matrizes 2x2** | 20 | Soma de Matrizes 2x2. | ✅ |
| **Histórico** | 23 | Exibe as últimas 10 operações realizadas. | ✅ |
| **Saída** | 24 | Encerra o programa. | ✅ |

### 🛑 Limitações Atuais

* **Matrizes**: A Multiplicação de Matrizes (opção 21) está no menu, mas ainda não foi implementada.
* **Funções Científicas**: Opções 11 a 19 estão reservadas para futuras implementações (ex: Raiz Cúbica, Log10, Média, etc.).
* **Fatorial**: O cálculo é limitado a $n \le 20$ para evitar o *overflow* do tipo `long double`.

---

## 🏗️ Estrutura do Projeto e Conceitos de C

Este projeto aplica as seguintes técnicas de programação em C:

### 1. Histórico Circular (Buffer FIFO)
* **Estrutura de Dados**: Utiliza a `struct Operacao` para armazenar o contexto completo de cada cálculo.
* **Gerenciamento**: Um array estático é gerenciado de forma circular por um índice, garantindo que as 10 operações mais recentes sejam sempre preservadas, substituindo a mais antiga quando o limite é atingido.

### 2. I/O Robusto e Tratamento de Erros
* **Validação de Entrada**: O programa verifica o retorno de `scanf()` para detectar e tratar entradas não numéricas.
* **Limpeza de Buffer**: Implementação da limpeza de *buffer* (`while (getchar() != '\n');`) para evitar problemas de leitura em comandos sequenciais.
* **Erros Matemáticos**: Uso de `NAN` (Not A Number) em `calc_divisao` e validações de domínio (números negativos para `sqrt`, zero ou negativos para `log`) para sinalizar operações inválidas.

---

## ⚙️ Como Compilar e Executar

Para construir e rodar a calculadora, você precisará de um compilador C (como GCC ou Clang) e da biblioteca de matemática padrão (`math.h`).

1.  **Salve o código**: Certifique-se de que o código-fonte está salvo em um arquivo, ex: `calculadora.c`.

2.  **Compile via Terminal**:
    O comando **deve** incluir a flag **`-lm`** (para linkar a biblioteca matemática).

    ```bash
    gcc calculadora.c -o calculadora -lm
    ```

3.  **Execute**:

    ```bash
    ./calculadora
    ```

---

## 🧑‍💻 Desenvolvedores e Contribuidores

Este projeto foi desenvolvido por um grupo de estudantes como parte de um trabalho de programação estruturada.

| Nome Completo | Função Principal | Repositório GitHub |
| :--- | :--- | :--- |
| **[kecia lidia pinheiro passos ]** | [ Desenvolvedor Principal] | [https://github.com/kecia0/CALCULADORAEM-C.git] |
| **[Amanda Freitas Rosencrantz Aiello]** | [Desenvolvedor Principal] | [https://github.com/usuario2] |
| 

