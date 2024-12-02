[link do video](https://www.loom.com/share/860700cc793745dd8ba79c9efa83a225)
---
# Algoritmo de Pilha

Um algoritmo de pilha é um algoritmo que utiliza uma pilha para realizar uma tradução. Uma pilha é uma estrutura de dados que organiza elementos em ordem inversa à ordem de inserção, ou seja, o último elemento adicionado é o primeiro a ser removido.

---

## Principais Operações

- **Push:** Adiciona um elemento ao topo da pilha.
- **Pop:** Remove o elemento do topo da pilha.
- **Peek:** Consulta o elemento no topo sem removê-lo.
- **IsEmpty:** Verifica se a pilha está vazia.
- **IsFull:** Verifica se a pilha está cheia (em implementações baseadas em arrays).

---

## Funcionamento

A pilha possui um "topo" que indica o índice do elemento mais recente. Para cada operação, manipulamos esse índice (top):

- **Adicionar (push):** Incrementa o topo e armazena o elemento.
- **Remover (pop):** Lê o valor no topo e decrementa o índice.
- **Consultar (peek):** Retorna o valor no índice do topo sem alterar o índice.

---

## Exemplo no Código

1. **Estrutura da Pilha**
    ```c
    typedef struct {
        int data[MAX];
        int top;
    } Stack;
    ```
    - `data:` Um array que armazena os elementos.
    - `top:` Índice do elemento no topo (inicialmente -1 para indicar que está vazia).

2. **Inicialização**
    ```c
    void initialize(Stack *stack) {
        stack->top = -1;
    }
    ```
    Define o topo como -1, indicando que não há elementos.

3. **Adicionar (Push)**
    ```c
    void push(Stack *stack, int value) {
        if (stack->top == MAX - 1) { // Checa se está cheia
            printf("Stack Overflow!\n");
            return;
        }
        stack->data[++stack->top] = value; // Incrementa o topo e armazena
    }
    ```
    Incrementa o índice top antes de adicionar o elemento. Se top for igual a MAX - 1, não é possível adicionar mais elementos.

4. **Remover (Pop)**
    ```c
    int pop(Stack *stack) {
        if (stack->top == -1) { // Checa se está vazia
            printf("Stack Underflow!\n");
            return -1; // Retorna um erro
        }
        return stack->data[stack->top--]; // Retorna o valor e decrementa o topo
    }
    ```
    Verifica se top é -1 para evitar remoção de elementos inexistentes. Retorna o elemento no topo e decrementa o índice.

5. **Consultar (Peek)**
    ```c
    int peek(Stack *stack) {
        if (stack->top == -1) {
            printf("Stack is empty!\n");
            return -1;
        }
        return stack->data[stack->top];
    }
    ```
    Apenas lê o valor no topo sem alterá-lo.

---

## Exemplo de Uso

Imagine que você está empilhando pratos: Você empilha um prato (push). Agora ele é o topo. Adiciona outro prato. Esse novo prato passa a ser o topo. Para remover um prato (pop), você tira o que está no topo. Se quiser ver o prato no topo sem removê-lo, você usa peek.

---

## Pontos Importantes

- **Controle de erros:**
    - Verificar se a pilha está cheia (overflow) antes de adicionar.
    - Verificar se está vazia (underflow) antes de remover.
- **LIFO:**
    - Sempre o último elemento inserido é o primeiro a sair.

---

## Aplicações

- Algoritmos de reversão de dados.
- Processamento de expressões matemáticas (parênteses, notação pós-fixa).
- Navegação em páginas da web (voltar e avançar).
