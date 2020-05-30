Gravity Sort
=================

De volta à Natureza
--------------------

Rozenberg desenhou o conceito que ficou conhecido como Computação Natural, que se trata de, a partir da observação de estruturas naturais, desenvolver estruturas computacionais.

O Gravity Sort faz parte de uma imensa gama de algoritmos com essas características, já que se baseia na força da gravidade para a sua concepção.

Ok, mas então vamos por fim apresentá-lo

Para entender a ideia podemos imaginar um caminhão carregado de caixa iguais, distribuídas em pilhas de diferentes alturas:

![caminhão](caminhão-2.png)

Agora imagine que o caminhão está subindo uma ladeira e que essas caixas deslizam em seu interior

>PERGUNTA: Desenhe como ficarão as caixas nessa situação

Ao terminar pode prosseguir

###

![caminhão vetor](caminhão-3.png)

Sim, as caixas agora estão organizadas em pilhas crescentes, e adotaram essa composição depois de serem puxadas para traz pela gravidade...daí o nome Gravity Sort

![meme_genio](meme.jpg)

Da mesma forma, se o caminhão estiver descendo a ladeira, as caixas se organizariam de forma decrescente

![caminhão vetor](caminhão-4.png)

Inicialmente esse algoritmo foi pensado para ser demonstrado com um [ábaco](https://pt.wikipedia.org/wiki/%C3%81baco), onde, em inglês, os discos que o compõe são chamados de “bead”, então esse algoritmo também pode ser encontrado como Bead Sort.

Mas enfim, como podemos traduzir essa movimentação que a gravidade proporciona para um código de ordenação?

Primeiro precisamos de um caminhão...

...mas calma, você não precisa criar um caminhão do zero, nos damos ele para você:

Passo 1: Construir o caminhão com a altura correta 
    def gravity_sort (input_list): 
            # Podemos representar o caminhão como uma lista
            # Onde cada elemento da lista é uma “pilha” e
            # cada "caixa" é representado com uma unidade 
            # nesse elemento, iniciamos a lista com zero em cada 
            # elemento representando o caminhão vazio


Passo 2: Primeiro loop -> Colocar as "caixas" no caminhão:
    def gravity_sort (input_list): 
        
        caminhao = [0] * max(input_list)
        return_list = []

        # Percorremos a lista de valores iniciais e para cada 
        # um deles fazemos um novo loop, nesse loop interno 
        # adicionamos 1 nas N primeiras posições da lista
        # isso funciona como empilhar as caixas da direita para
        # esquerda em cada uma das colunas.
        
        for num in input_list:
            for i in range(num):
                caminhao[i] += 1
   

Passo 3: Para o passo 3, precisariamos "girar o caminhão", mas isso não é prático computacionalmente (acredito que nem na vida real)

>Você consegue imaginar como "girar" esse caminhão?

###

A forma que encontramos não seria "girar exatamente", computacionalmente, obtemos o resultado esperado fazendo a contagem ao retirar uma caixa da cada pilha, e colocando-o em um outra lista.
O valor resultante dessa contagem é igual ao maior elemento da lista.

Abaixo está o código da implementação completa:
    
    def gravity_sort (input_list): 

        caminhao = [0] * max(input_list)
        for num in input_list:
            for i in range(num):
                caminhao[i] += 1
        for j in input_list:
            sum = 0
        for n in transposed_list:
            if(n > 0):
                sum += 1
        return_list.append(sum)
        for n,elem in enumerate(transposed_list):
            transposedlist[n] -= 1
        print("return",,returnlist)
        print("Transposed",,transposed_list)

    return return_list



Apesar de ser um algoritmo bem interessante, ele possui algumas limitações, que podem ser comparadas até com a sua inspiração do mundo real.

Da mesma forma que a caixa precisa ser dotada de massa para sofrer a ação da gravidade, o Gravity Sort necessita que os numeros de entrada sejam positivos.
Mas ainda assim é possível trabalhar com numeros negativos com esse algoritimo

>Você consegue pensar em um estratétgia para escapar dessa limitação?


**Valide sua resporta

> Fim do handout. Não fuja! Teremos um fechamento!


