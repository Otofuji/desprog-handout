Gravity Sort
=================

De volta à Natureza
--------------------

Você certamente já deve ter ouvido a essa altura do campeonado falar de Dijkstra. Caso não, ele foi um importante cientista da computação holandês que fez importantes contribuições com o desenvolvimento de algoritmos e linguagens de programação. Dijkstra disse:

    Nossos sistemas são muito mais complicados do que 
    poderia ser considerado saudável, e são bagunçados 
    e caóticos demais para serem usados com conforto e 
    confiança. (...) Complexidade não dominada é a raiz 
    da miséria.

    -- E. W. Dijkstra

A partir disso, Rozenberg desenvolveu um conceito chamado que ele chamou de Computação Natural. Ou seja, observar intuitivamente algo na Natureza e usar essa ideia simples para implementar um algoritmo. E o Gravity Sort usa justamente isso: seu princípio de funcionamento é algo simples e intuitivo. 

![caminhão](caminhão-1.png)

Veja: imagine um caminhão com algumas caixas empilhadas dentro dele em uma dada ordem. O caminhão não está lotado, apenas com algumas caixas. Porém, bate um vento forte nele e o caminhão tomba.



>PERGUNTA: O que acontecerá com as caixas que estavam em pé quando o caminhão tombou, por efeito da gravidade?

**Dica**: se a resposta não vier à sua mente em até um minuto, pule para ver a resposta. Não precisa validar esta resposta.

***

Prossiga após ter pensado na resposta ou ter passado mais de um minuto.



###

Uma maçã caindo no cocoruto
--------------------

![tombado](90.jpeg)

Isso mesmo, as caixas tombarão também. Mais do que isso, ficarão dispostas numa ordem diferente da que estavam antes do caminhão tombar. Será que podemos usar essa ideia para que esse tombamento seja útil de alguma forma? 

Arulanandham *(quero ver você pronunciar esse nome)*, Calude e Dinneen, autores do Gravity Sort, diriam que sim. 

Vamos continuar pensando nas caixas do baú de um caminhão. Cada pilha de caixas representa um índice de um vetor e a quantidade de caixas em cada pilha representa o valor de cada índice do vetor. 

![caminhão vetor](caminhão-2.png)

Sem manipular cada caixa, pense numa forma de, apenas inclinando o caminhão, ordenar crescentemente esse vetor, usando essa ideia de que cada coluna representa um índice.

Ou seja, não pode abrir a caçamba e reorganizar, mas pode inclinar o caminhão para os lados para que as caixas deslizem dentro do baú.

>PERGUNTA: Que movimento(s) você precisa fazer para que fiquem ordenados em ordem crescente?

***

Não continue até ser validado.


###

Ladeiras
--------------------

![caminhão subindo](caminhão-3.png)

Muito bem, sabemos que se inclinarmos o caminhão para a direita (ou colocá-lo numa ladeira acima) as caixas deslizarão até que as pilhas fiquem ordenadas em ordem crescente de altura.



Usando essa mesma ideia, será que conseguimos ordenar as pilhas de caixas na ordem decrescente?

Ou seja, não pode abrir a caçamba e reorganizar, mas pode inclinar o caminhão para os lados para que as caixas deslizem dentro do baú.

>PERGUNTA: Que movimento(s) você precisa fazer para que fiquem ordenados em ordem decrescente?

***

Não continue até ser validado.



###

A ideia central
--------------------

![caminhão descendo](caminhão-4.png)

Essa é a ideia central do funcionamento do Gravity Sort. Esse algoritmo também é chamado de Bead Sort, pois em inglês os discos do ábaco são assim chamados. Isso porque a primeira vez que esse conceito foi apresentado foi usando um ábaco para ilustrar. Para os dois nomes, o algoritmo é o mesmo. Existindo uma estrutura como a do ábaco, basta girar ela para se obter o vetor ordenado crescente ou decrescentemente. 



Agora que entendemos a ideia intuitiva por trás do Gravity Sort, vamos começar a pensar em formas de transformar essa ideia em algo implementável computacionalmente.

***

>PERGUNTA: Se estamos lidando com o conteúdo de cada índice do vetor como o número de discos existentes no ábaco, será que existe algum tipo de restrição quanto a que tipo de conteúdo do vetor o Gravity Sort funciona?

**Dica**: pense em vetores com números inteiros positivos, inteiros negativos, ponto flutuante, imaginários, strings etc., e tente imaginar como o algoritmo reagiria a esse tipo de entrada.

***

Não continue até ser validado.




###

Implementando
--------------------
Essa é a maior restrição do Gravity Sort. Ele funciona bem, mas apenas para vetores contendo exclusivamente números inteiros positivos. 

Mas… Claro, podemos pensar em algumas alternativas de gambiarra para adaptar o código para *contornar essas limitações*. Por exemplo, ao lidar com números negativos, podemos ter um número que soma o maior número negativo de forma a ele ficar positivo, ordena pelo Gravity Sort e então subtrai esse mesmo valor que foi somado para termos os valores originais. *Sempre há um jeito de contornar limitações específicas.* 

Vamos seguir pensando em nossa implementação, mas apenas pensando em vetores contendo números inteiros e positivos, por enquanto, para facilitar.

De acordo com a [Wikipédia](https://en.wikipedia.org/wiki/Bead_sort#Implementation), podemos pensar em uma lista em Python com uma sequência de inteiros. A função retorna uma nova lista (ao invés de transmutar na própria lista de entrada), embora seja possível para uma operação *inplace*.

>Não abra o link da Wikipédia ainda. Ele contém spoilers. E quem recebe spoilers no handout, receberá spoilers de todas as séries por 12 anos.


CONTINUAR

A PARTIR

DAQUI

***

ATIVIDADES PARA ENTENDER
A IMPLEMENTAÇÃO DO ALGORITMO










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