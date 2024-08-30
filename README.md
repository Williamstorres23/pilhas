# Pilhas em C

## Introdução

Uma **pilha** é uma estrutura de dados que segue o princípio LIFO (Last In, First Out), o que significa que o último item a ser adicionado é o primeiro a ser removido. Pilhas são amplamente utilizadas em algoritmos, manipulação de expressões matemáticas, e na gestão de chamadas de funções em linguagens de programação.

Este repositório fornece implementações básicas de pilhas em C, utilizando duas abordagens: uma com um array e outra com uma estrutura ligada.

## Estrutura de Dados Pilha

### 1. Implementação com Array

A pilha é implementada utilizando um array de tamanho fixo. A seguir, estão as funções principais para manipulação da pilha:

- **Inicializar a Pilha**
- **Empilhar (Adicionar Item)**
- **Desempilhar (Remover Item)**
- **Verificar se a Pilha está Vazia**
- **Verificar se a Pilha está Cheia**
- **Visualizar o Topo da Pilha**

### 1. Implementação com Estrutura Ligada

Nesta abordagem, a pilha é implementada utilizando uma lista ligada, permitindo tamanhos dinâmicos para a pilha.

#### Código

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Nodo {
    int dado;
    struct Nodo *proximo;
} Nodo;

typedef struct {
    Nodo *topo;
} Pilha;

void inicializarPilha(Pilha *p) {
    p->topo = NULL;
}

int pilhaVazia(Pilha *p) {
    return p->topo == NULL;
}

void empilhar(Pilha *p, int item) {
    Nodo *novo = (Nodo*)malloc(sizeof(Nodo));
    if (novo == NULL) {
        printf("Erro ao alocar memória!\n");
        return;
    }
    novo->dado = item;
    novo->proximo = p->topo;
    p->topo = novo;
}

int desempilhar(Pilha *p) {
    if (pilhaVazia(p)) {
        printf("Pilha vazia!\n");
        return -1; // Retorna um valor de erro
    }
    Nodo *temp = p->topo;
    int valor = temp->dado;
    p->topo = temp->proximo;
    free(temp);
    return valor;
}

int topoPilha(Pilha *p) {
    if (pilhaVazia(p)) {
        printf("Pilha vazia!\n");
        return -1; // Retorna um valor de erro
    }
    return p->topo->dado;
}

int main() {
    Pilha p;
    inicializarPilha(&p);

    empilhar(&p, 10);
    empilhar(&p, 20);
    empilhar(&p, 30);

    printf("Topo: %d\n", topoPilha(&p));

    printf("Desempilhado: %d\n", desempilhar(&p));
    printf("Desempilhado: %d\n", desempilhar(&p));
    printf("Desempilhado: %d\n", desempilhar(&p));
    printf("Desempilhado: %d\n", desempilhar(&p)); // Deve indicar que a pilha está vazia

    return 0;
}
```

## Compilação e Execução

Para compilar e executar os exemplos, você pode usar o comando `gcc`:

```bash
gcc -o pilha_array pilha_array.c
./pilha_array
```

```bash
gcc -o pilha_ligada pilha_ligada.c
./pilha_ligada
```

Substitua `pilha_array.c` e `pilha_ligada.c` pelos nomes dos arquivos que contêm o código.

## Conclusão

As pilhas são uma estrutura de dados fundamental que pode ser implementada de várias maneiras, dependendo das necessidades da aplicação. Este repositório fornece exemplos básicos para ajudar a entender o funcionamento e a implementação das pilhas em C.

Se você tiver dúvidas ou sugestões, sinta-se à vontade para abrir uma issue ou contribuir com o código!
