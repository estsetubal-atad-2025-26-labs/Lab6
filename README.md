# Algoritmos e Tipos Abstratos de Dados

## Lab 6 - Utilização do ADT Stack

### 🎯 Objetivos:

* Parametrização e utilização do ADT Stack.

📚  **Referências**:

- Slides das aulas TP;
  
- Capítulo 4 do livro “Tipos Abstratos de Dados – Linguagem C. Bruno Silva”, disponível no Moodle (Secções 4, 4.1, 4.2 e 4.3).

### Introdução

O ADT Stack, ou tipo abstrato de dados *pilha*, é uma coleção fundamental em programação que segue o princípio LIFO (Last In, First Out) - o último elemento a entrar é o primeiro a sair. Este comportamento é semelhante a uma pilha de pratos: só é possível adicionar ou remover elementos pelo topo.

A especificação do ADT Stack expõe um conjunto de operações bem definidas, como `stackPush` (inserir elemento), `stackPop` (remover elemento) e `stackPeek` (consultar o elemento no topo). Esta abstração permite que o utilizador interaja com uma pilha sem precisar de conhecer a sua implementação concreta, que pode ser baseada em arrays ou listas ligadas.

O ADT Stack é amplamente utilizado em diversas áreas da computação, incluindo avaliação de expressões, controlo de chamadas de funções (call stack), algoritmos de backtracking e navegação em estruturas como árvores e grafos.

O objetivo deste laboratório é utilizar o ADT Stack, dada a sua especificação no ficheiro `stack.h` e uma implementação fornecida (da qual não necessitamos conhecer detalhes).


#### Parametrização da ADT Stack

A parametrização do tipo de dados a guardar nas instâncias de ADT Stack é feita nos ficheiros (módulo) `stackElem.h e stackElem.c`, nomedamente através da definição (*typedef*) do tipo `StackElem` e da função `stackElemPrint`.

Não é possível, desta forma, no mesmo programa termos duas pilhas que guardem tipos de dados diferentes.

> [!IMPORTANT]
>
> Para cada um dos exercícios seguintes deverá *clonar* o projeto base [ADTStack_Template](https://github.com/estsetubal-atad/ADTStack_Template), também utilizado na TP.
>

---

### 1 | Processamento de números com recurso a duas stacks

> [!TIP]
> Com este exercício pretende-se que consolide o modo de funcionamento de uma pilha. Durante a codificação responda às questões incluídas.

Clone o repositório base e implemente um programa nas condições apresentadas de seguida.

#### Parametrização

Deverá parametrizar o ADT Stack para armazenar números reais.

#### Programa

O programa deve realizar as seguintes operações:

1. Ler do utilizador uma sequência de números reais, terminada pelo valor `0` (o valor `0` não deve ser armazenado).

2. Armazenar os valores introduzidos numa stack (`s1`).
   
- ❓ Depois de todos os elementos se encontrarem na pilha, o elemento que se encontra no topo foi o *primeiro* ou *último* que o utilizador inseriu? Se formos agora remover todos os elementos, qual a ordem pela qual serão apresentados?

3. Transferir todos os elementos de `s1` para uma segunda stack (`s2`).
   - Durante esta transferência, os valores devem ser apresentados no ecrã à medida que são removidos de `s1`.

4. Após a transferência, considerar o elemento no topo de `s2`:

   * Se for **positivo**, o programa deve calcular a **média** de todos os valores;
   * Se for **negativo**, o programa deve calcular a **soma** de todos os valores.

- ❓ O elemento que se encontra no topo de `s2` foi o *primeiro* ou *último* que o utilizador inseriu?

5. O cálculo do passo anterior deve ser realizado recorrendo à remoção dos elementos da stack `s2`.

6. No final, apresentar o resultado obtido.

**Notas:**

* Ambas as stacks devem ficar vazias no final da execução.
* Deve garantir a correta gestão de memória dinâmica.

---

### 2 | Movimentos bancários com funcionalidade de “undo”

> [!TIP]
> Com este exercício pretende-se que compreenda que as pilhas são utilizadas em todas as situações em que seja necessário "desfazer" acções, pois no topo da pilha estará sempre a última ação efetuada.
>
> O programa irá manter um saldo de conta e um histórico de movimentos bancários.
>

Clone o repositório base e implemente um programa nas condições apresentadas de seguida. Leia o problema proposto até ao fim e, se possível, tente decompô-lo em funções.

#### Definição de tipo de dados e parametrização

Deve começar por definir **um tipo estruturado, e.g., `Movimento`, que represente um movimento bancário**, contendo:

* o "valor" do movimento (em euros);
* o "tipo de operação", representado por:

  * `1` para depósito;
  * `-1` para levantamento.


Deverá parametrizar o ADT Stack para armazenar elementos do tipo `Movimento`.

#### Programa

O programa deve realizar as operações descritas de seguida, 

1. Inicializar o saldo (número real) de uma conta bancária a `0`.

2. Ler do utilizador uma sequência de movimentos bancários. Para cada movimento, deverá ler seu o valor e tipo de movimento e criar uma instância do tipo `Movimento`.

   - A introdução termina quando o utilizador introduzir o valor `0` num dado movimento.

3. À medida que os movimentos são introduzidos:

   * devem ser armazenados numa stack;
   * o saldo deve ser atualizado de acordo com o tipo de operação;
   * o saldo atual deve ser apresentado após cada movimento.

4. Após a introdução de dados:

   * apresentar o número total de operações realizadas (tamanho da stack);
   * perguntar ao utilizador quantas operações pretende desfazer.

5. Efetuar a operação de “undo” o número de vezes indicado, removendo elementos da stack:

   * por cada movimento removido, o saldo deve ser atualizado no sentido inverso:

     * depósito -> subtrair ao saldo;
     * levantamento -> somar ao saldo;
   * o saldo atualizado deve ser apresentado após cada operação de “undo”.

**Notas:**

* Deve garantir que não são realizadas mais operações de “undo” do que o número de elementos existente na stack.
* No final, a stack deve conter apenas os movimentos que não foram desfeitos.
* Deve garantir a correta gestão de memória dinâmica.

---
<bruno.silva@estsetubal.ips.pt> & <anibal.ponte@estsetubal.ips.pt>

