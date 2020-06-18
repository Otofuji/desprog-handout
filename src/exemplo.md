Gravity Sort
=================

O Gravity Sort faz parte de uma imensa gama de algoritmos com essas características, já que se baseia na força da gravidade para a sua concepção. Vamos por fim apresentá-lo.

Para entender a ideia podemos imaginar um caminhão carregado de caixa iguais, distribuídas em pilhas de diferentes alturas:

![caminho](Novo-caminho.png)

Agora, imagine que o caminhão está subindo uma ladeira e que essas caixas deslizam em seu interior.

>PERGUNTA: Desenhe como ficarão as caixas nessa situação

Ao terminar, pode prosseguir. Não precisa validar esta resposta.

###

A gravidade funciona
--------------------

![caminho vetor](Novo-caminho-2.png)

Sim, as caixas agora estão organizadas em pilhas crescentes, e adotaram essa composição depois de serem puxadas para trás pela gravidade… **daí o nome Gravity Sort!**

![meme_genio](meme.jpg)

Da mesma forma, se o caminhão estiver descendo a ladeira, as caixas se organizariam de forma decrescente.

Inicialmente, esse algoritmo foi pensado para ser demonstrado com um [ábaco](https://pt.wikipedia.org/wiki/%C3%81baco), onde, em inglês, os discos que o compõe são chamados de “bead”. Por isso, este mesmo algoritmo também pode ser chamado de Bead Sort.

Enfim, como podemos traduzir essa movimentação que a gravidade proporciona para um código de ordenação?

Antes de pensar na implementação, vamos pensar em como podemos transmutar essa analogia das caixas do caminhão. 

**Talvez as imagens dos caminhões que apareceram antes contenham algum *spoiler* que te ajude a pensar.**

>PERGUNTA: pensando em vetores, o que são são os índices do vetor e o que são os valores em cada caixa?

Valide a resposta antes de prosseguir.

###

Implementação
--------------------

Cada pilha é um índice do vetor, e a quantidade de caixas em cada pilha é o valor em cada índice.

Vamos agora seguir para a implementação do algoritmo. Primeiro precisamos de um caminhão…

…mas calma, você não precisa criar um caminhão do zero. Nós damos ele para você:

**Passo 1: Preenchendo o caminhão:**

A função recebe uma lista de entrada, onde cada valor da lista representa o número de caixas presente em cada pilha. Lista porque trabalharemos com uma implementação em Python no handout.
    
    def gravity_sort (input_list): 

            

**Passo 2: Primeiro loop -> Inclinando o caminhão:**

A partir da lista de entrada, se observarmos a disposição das caixas a partir da traseira do caminhão, temos uma lista que pode ser chamada de `lista de acumulação`, onde cada valor dessa lista é referente à disposição das caixas nesse novo ponto de vista.
    
    def gravity_sort (input_list): 
        
        return_list = []
        transposed_list = [0] * max(input_list)
        
        for num in input_list:
            for i in range(num):
                transposed_list[i] += 1
            print(num,transposed_list)

>PERGUNTA: o que está acontecendo com o caminhão na lista de acumulação?

Valide a resposta antes de prosseguir.

###

Um outro ponto de vista
--------------------
   
![Vetor de acumulao](Novo-caminho-3.png)

Você pode não ter notado, mas existe uma relação direta entre o maior valor existente na lista de entrada e o tamanho do vetor de acumulação… **eles são os mesmos!** Isso será importante quando discutirmos sobre complexidade. 

Repare olhando para essa imagem aqui em cima com as imagens que você viu na sessão anterior. O caminhão é o mesmo e as caixas são as mesmas. Apenas estamos olhando por *um outro ponto de vista*. 

Vamos continuar com os passos.

**Passo 3: Segundo loop -> Contando as caixas:**

A partir do vetor de acumulação, se retirarmos uma caixa de cada pilha e as somarmos temos um resultado interssante.

    def gravity_sort(input_list):
        
        print("Lista entrada")
        print(input_list)
        print("--------------------------------")
        
        return_list = []
        transposed_list = [0] * max(input_list)
        
        print("Loop 1")
        
        for num in input_list:
            for i in range(num):
                transposed_list[i] += 1
            print(num,transposed_list)
                
        
        print("--------------------------------")
        print("Loop 2")


Com a nova disposição de caixas da lista de acumulação, o segundo loop é responsável por retirar uma caixa de cada uma das pilhas e somar a quantidade, guardando esse valor da soma em um vetor a ser retornado.

>Implemente o segundo loop como descrito acima.

Valide a resposta antes de prosseguir. Peça ajuda se travar. 

###

Habemus Gravity Sort
--------------------

Com a implementação do segundo loop, já temos nosso código completo.
    
    def gravity_sort_traduzido(input_list):

        print("--------------------------------")

        return_list = []
        transposed_list = [0] * max(input_list)
        
        print("Loop 1")
        
        for num in input_list:
            for i in range(num):
                transposed_list[i] += 1
        
        print("--------------------------------")
        print("Loop 2")

        for _ in input_list:

            sum = 0
            for n in transposed_list:
                if(n > 0): 
                    sum += 1
            return_list.append(sum)

            for n,elem in enumerate(transposed_list):
                transposed_list[n] -= 1

    return return_list

Um detalhe interessante no segundo loop é o check de `n > 0`, que pode ter passado despercebido por alguns. Essa verificação só existe porque estamos trabalhando com um sistema inspirado no mundo físico. Logo, quando `n` chega zero, significa que não há mais caixas na pilha. Apesar do loop continuar subtraindo uma caixa de cada andar, apenas os números positivos são considerados na contagem.

Mas, afinal, qual é a saída desse algoritmo?

>Simule o resultado da return_lista com a entrada apresentada no exemplo inicial.

Valide a resposta antes de prosseguir.

###

Vamos para os finalmente: output
--------------------

~ Gif com o resultado aqui ~

Apesar de ser um algoritmo bem interessante, ele possui algumas limitações, que podem ser comparadas até com a sua inspiração do mundo real.

Da mesma forma que a caixa precisa ser dotada de massa para sofrer a ação da gravidade, o Gravity Sort necessita que os números de entrada sejam positivos. Mas ainda assim é possível trabalhar com numeros negativos com esse algoritimo

>Você consegue pensar em um estratégia para escapar dessa limitação?

###

Complexo?
--------------------

Sim, se fizermos uma transformação somando os números negativos por um offset para que até mesmo o menor deles fique positivo, trabalharmos com o Gravity Sort e depois "desconverter" esses números usando esse mesmo offset, conseguiremos o que queremos! Essa é a beleza da computação: *sempre há uma gambiarra para qualquer coisa.*

Agora que temos a ideia do Gravity Sort, e sua implementação, podemos falar sobre a complexidade deste algoritmo.

>Discuta com seu grupo acerca da complexidade do Gravity Sort

*Lembre-se da relação existente entre o vetor de entrada e o vetor de acumulação.

**Valide sua resposta

###

Complexidade do Gravity Sort
--------------------

Nessa implementação, temos dois loops. Vamos analisá-los separadamente:

O primeiro loop:
    
    for num in input_list:
            for i in range(num):
                transposed_list[i] += 1

Esse tem seu número de execuções igual à soma de todos os valores na input list. Podemos dizer que é um `O(s)`, onde `s` representa essa soma de valores;

No segundo loop:

    for _ in input_list:

                sum = 0
                for n in transposed_list:
                    if(n > 0): 
                        sum += 1
                return_list.append(sum)

                for n,elem in enumerate(transposed_list):
                    transposed_list[n] -= 1

Temos esse loop, com outros dois loops dentro. Vamos chamá-los de `loop a` e `loop b`, respectivamente. O `loop a` tem uma complexidade `O(n(max_num))`, já que é executado `n` vezes para o tamanho da `transposed_list`, que sabemos que é igual ao maior valor de entrada. Para o `loop b`, temos um situação semelhante ao primeiro, em que é `O(n(max_num))`. Portanto, para o segundo loop, temos uma complexidade `O(2n*num_max)`.

Para o algoritmo completo temos uma complexidade igual a `O(s+2n*max_num)`.

É possível simplificar essa complexidade para `O(n*max_num)`, já que a soma e a multiplicação de constantes não afetam o tempo de processamento. Porém não podemos desprezar o termo `max_num`, onde para uma entrada pequena com grandes valores, a lista de acumulação se torna automaticamente grande, o que eleva o tempo de processamento.

> Fim do handout.


