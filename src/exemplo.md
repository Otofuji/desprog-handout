Gravity Sort
=================

De volta à Natureza
--------------------

Você já deve ter ouvido falar Dijkstra, um importante cientista da computação, que teve importantes contribuições para o desenvolvimento de algoritmos e linguagens de programação. A partir das ideias de Dijkstra, Rozenberg desenhou o conceito que ficou conhecido como Computação Natural, que se trata de, a partir da observação de estruturas naturais, desenvolver estruturas computacionais.

O Gravity Sort faz parte de uma imensa gama de algoritmos com essas características, já que se baseia na força da gravidade para a sua concepção.

Ok, mas então vamos por fim apresentá-lo

Para entender a ideia podemos imaginar um caminhão carregado de caixa iguais, distribuídas em pilhas de diferentes alturas:

![caminhão](caminhão-2.png)

Veja: imagine um caminhão com algumas caixas empilhadas dentro dele em uma dada ordem. O caminhão não está lotado, apenas com algumas caixas. Porém, bate um vento forte nele e o caminhão tomba.

Agora imagine que o caminhão está subindo uma ladeira e que essas caixas deslizam em seu interior

>PERGUNTA: Consegue Imaginar como as caixas ficarão dispostas?

###

![caminhão vetor](caminhão-3.png)

Sim, as caixas agora estão organizadas em pilhas crescentes, e adotaram essa composição depois de serem puxadas para traz pela gravidade...daí o nome Gravity Sort

![meme_genio](meme.jpg)

Inicialmente esse algoritmo foi pensado para ser demonstrado com um [ábaco](https://pt.wikipedia.org/wiki/%C3%81baco), onde, em inglês, os discos que o compõe são chamados de “bead”, então esse algoritmo também pode ser encontrado como Bead Sort.

Mas enfim, como podemos traduzir essa movimentação que a gravidade proporciona para um código de ordenação?

Primeiro precisamos de um caminhão...

...mas calma, você não precisa criar um caminhão do zero, nos damos ele para você:

    def gravity_sort (input_list):

        # Passo 1: Construir o ábaco com a altura correta    
            # Podemos representar o caminhão como uma lista
            # Onde cada elemento da lista é uma “pilha” e
            # cada "caixa" é representado com uma unidade nesse elemento 
            # iniciamos a lista com zero em cada elemento representando o caminhão vazio
        
        # Passo 2: Primeiro loop -> Colocar as "caixas" no caminhão
            # Percorremos a lista de valores iniciais e para cada um deles fazemos um novo loop
            # nesse loop interno adicionamos 1 nas N primeiras posições da lista
            # isso funciona como colocar empilhar as caixas em diferentes colunas.

        #Passo 3: 
        












###

>Resto do handout anterior. Não será usado. 

    def gravity_sort(input_list):
    
        return_list = []
        
        transposed_list = [0] * max(input_list)
        
        for num in input_list:
            transposed_list[:num] = [n + 1 for n in transposed_list[:num]]

        for _ in input_list:
            return_list.append(sum(n > 0 for n in transposed_list))
            transposed_list = [n - 1 for n in transposed_list]

        return return_list

Vamos destrinchar o que está acontecendo aqui. Como dissemos, não faremos uma operação *inplace*, mas sim retornaremos uma nova lista ordenada após a operação do Gravity Sort. Por isso, chamamos `return_list = []` e inicializamos uma lista transporta `transposed_list = [0] * max(input_list)` que é tão alta quanto o maior valor existente na lista. Isso é para podermos simular o tal do ábaco.

Nessa implementação em software, temos dois loops `for`. Vamos analisar um por um.

No primeiro `for`, 

    for num in input_list:
        transposed_list[:num] = [n + 1 for n in transposed_list[:num]]

estamos vendo para cada elemento da lista de entrada (cada coluna do ábaco), estamos incrementando tantos elementos da `transposed_list` quanto à sua altura. Neste loop, estamos virando o ábaco de lado para que o efeito da gravidade atue. 

Agora que os discos caíram, precisamos des-transpor para termos uma lista normal novamente. Para isso, contamos a partir da linha mais baixa dos discos de ábaco caídos e removemos essa linha subtraindo 1 de cada coluna da `transposed_list`. Quando a coluna não é alta o suficiente para a linha atual, seu valor na `transposed_list`será menor que zero. Ou seja:

    for _ in input_list:
        return_list.append(sum(n > 0 for n in transposed_list))
        transposed_list = [n - 1 for n in transposed_list]

Contando valores maiores que zero é a forma que temos de dizer quantos discos estão na linha mais baixa. Em Python, booleanos podem ser avaliados como inteiros. Ou seja: `True == 1` e `False == 0`. Removemos a linha mais baixa ao subtrair 1 de cada elemento.

Nesta implementação, a lista retornada está ordenada em ordem decrescente. Voltando para a ideia do ábaco, é como se tivéssemos girado o ábaco para a esquerda, ao invés da direita. Isso mostra que podemos ordenar tanto de um lado quanto do outro

>PERGUNTA: Sabemos que originalmente o Gravity Sort foi pensado como uma implementação em hardware. Se o Gravity Sort é tão simples e intuitivo e tão bom em complexidade, por que ele não é amplamente usado, assim como o Quick Sort, por exemplo?

**Dica**: Observe a implementação apresentada em Python e tente ver qual complexidade o algoritmo fica implementando dessa forma para entradas particularmente grandes. Essa é uma complexidade linear?

***

Não continue até ser validado.




###

> Fim do handout. Não fuja! Teremos um fechamento!