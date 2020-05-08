Gravity Sort
=================

Aquecendo o carburador
--------------------
Hoje trataremos do Gravity Sort, um algoritmo de ordenação de vetores que, como o nome sugere, utiliza a gravidade. Para começar, vamos aquecer com alguns conceitos importantes vistos anteriormente.

    >PREVIOUSLY, ON INSPER ENGINEERING…

Considere a Segunda Lei e a Lei da Gravitação Universal, ambas de Newton, dadas por, e igualando em uma única equação:

$$$\vec{F}=m\vec{a}=\ -\frac{GM}{r^2}\hat{r}$$$

Cancelando a massa em ambos os lados da equação e escrevendo a aceleração e a derivada segunda da distância entre os corpos em termos de equações escalares de movimento, percebe-se que há conservação do momento angular $$L$$, obtendo-se facilmente:

$$$\ddot{r}=\ \frac{L^2}{m^2r^3}=\ -\frac{GM}{r^2}$$$

Essa equação diferencial de $$r$$ em função de $$t$$ pode ser modificada de modo que $$r$$ seja uma função de $$Θ$$ modificando a segunda derivada temporal através da regra da cadeia, resulta, então, a equação para a função $$r(Θ)$$ da qual se deriva para a equação do oscilador harmônico. Simplificando para a constante $$ε$$, denominada de constante da excentricidade orbital, chegamos em:

$$$r\left(\Theta\right)=\ \left(\frac{L^2}{{GMm}^2}\right)\left(\frac{1}{1+\varepsilon\cos(\Theta-\delta)}\right)$$$

Agora ficou fácil! 

>PERGUNTA: Observando a última equação, é possível chegar 
em uma conclusão muito importante. Você sabe qual é?

**Dica:** se a resposta não vier à sua mente em até um minuto, pule para ver a resposta. Não precisa validar esta resposta.

***

Prossiga após ter pensado na resposta ou ter passado mais de um minuto.



###

O cabeçote queimou
--------------------
*Ah, que saudade desse cheiro de neurônio queimado… A última vez que senti esse cheiro faz tempo: foi ontem, fazendo embarcados.*

Se você não conseguiu chegar em uma conclusão, não se desespere. Não era para chegar em conclusão alguma. A demonstração acima foi propositalmente feita pulando vários passos apenas para confundir. 
    
>IMAGEM MEME NAZARÉ AQUI

Talvez ficasse mais claro se fizéssemos uma demonstração mais detalhada sem pular os passos. Afinal, tudo isso lhe parece familiar, não é mesmo? Trabalhamos semestre passado com a Lei da Gravitação Universal na aula 2 de Eletromag e você deve se lembrar disso. Ou talvez não... não vou te julgar se você não lembra dessa aula em específico de 7 de agosto de 2019. 

**O ponto é:** mesmo para nós que já passamos por disciplinas que fazem uso ostensivo da matemática e da física e, se estamos aqui hoje, conseguimos sobreviver a isso (ainda bem!), olhar para uma demonstração de algumas equações não parece dar uma ideia muito clara sobre como funciona um algoritmo. 

Você certamente já deve ter ouvido falar de Dijkstra. Caso não, ele foi um importante cientista da computação holandês que fez importantes contribuições com o desenvolvimento de algoritmos e linguagens de programação. Não foi ele quem desenvolveu o Gravity Sort, mas os autores desse algoritmo fizeram uma citação dele no artigo em que publicaram ele. Dijkstra disse:

    Nossos sistemas são muito mais complicados do que 
    poderia ser considerado saudável, e são bagunçados 
    e caóticos demais para serem usados com conforto e 
    confiança. (...) Complexidade não dominada é a raiz 
    da miséria.

    -- E. W. Dijkstra

A partir disso, Rozenberg desenvolveu um conceito chamado que ele chamou de Computação Natural. Ou seja, se a matemática é capaz de descrever a Natureza, como vimos nas disciplinas anteriores que é possível, o contrário deve ser válido: ir de volta à Natureza, observar intuitivamente algo e usar essa ideia simples para implementar um algoritmo. 

Afinal, começar pelo complicado significa não entender ou entender superficialmente e, como disse Dijkstra, é a raiz da miséria. Então, vamos começar com uma ideia simples (a ponto que até uma criança de 5 anos seja capaz de entender)* e evoluir para entender o funcionamento do Gravity Sort. 

*Dessa vez não estou zoando com sua cara!

Imagine um caminhão com algumas caixas empilhadas dentro dele em uma dada ordem. O caminhão não está lotado, apenas com algumas caixas. Durante o trajeto, esse caminhão sofre um acidente e tomba. 

>PERGUNTA: O que acontecerá com as caixas que estavam em pé quando o caminhão tombou, por efeito da gravidade?

**Dica**: se a resposta não vier à sua mente em até um minuto, pule para ver a resposta. Não precisa validar esta resposta.

***

Prossiga após ter pensado na resposta ou ter passado mais de um minuto.



###

Uma maçã caindo no cocoruto
--------------------
Isso mesmo, as caixas tombarão também. Mais do que isso, ficarão dispostas numa ordem diferente da que estavam antes do caminhão tombar. Será que podemos usar essa ideia para que esse tombamento seja útil de alguma forma? Arulanandham (quero ver você pronunciar esse nome), Calude e Dinneen, autores do Gravity Sort, diriam que sim. 

Vamos começar pensando numa coisa um pouco mais organizada que o baú de um caminhão. Um ábaco, disposto como na imagem. Cada coluna imaginária representa um índice de um vetor e a quantidade de discos em cada coluna imaginária representa o valor do inteiro positivo existente em cada índice do vetor. 

>IMAGEM ÁBACO AQUI

Sem manipular cada disco, pense numa forma de, apenas usando a gravidade, ordenar crescentemente esse vetor, usando essa ideia de que cada coluna representa um índice.

Ou seja, não pode colocar os dedos nos discos, mas você pode girar o ábaco à vontade até os discos ficarem ordenados crescentemente.

>PERGUNTA: Que movimento você precisa fazer para que fiquem ordenados?

***

Não continue até ser validado.



###

A ideia central
--------------------
Essa é a ideia central do funcionamento do Gravity Sort. Esse algoritmo também é chamado de Bead Sort, pois em inglês os discos do ábaco são assim chamados. Para os dois nomes, o algoritmo é o mesmo. Existindo uma estrutura como a do ábaco, basta girar ela para se obter o vetor ordenado crescente ou decrescentemente. 

Aqui uma animação que representa a ideia.

>ANIMAÇÃO ÁBACO AQUI

Aqui outra animação que representa o algoritmo para entradas maiores.

>ANIMAÇÃO ALGORITMO AQUI

***

>PERGUNTA: Se estamos lidando com o conteúdo de cada índice do vetor como o número de discos existentes no ábaco, será que existe algum tipo de restrição quanto a que tipo de conteúdo do vetor o Gravity Sort funciona?

**Dica**: pense em vetores com números inteiros positivos, inteiros negativos, ponto flutuante, imaginários, strings etc., e tente imaginar como o algoritmo reagiria a esse tipo de entrada.

***

Não continue até ser validado.




###

Implementando
--------------------
Essa é a maior restrição do Gravity Sort. Ele funciona bem, mas apenas para vetores contendo exclusivamente números inteiros positivos. Para qualquer coisa diferente disso, a lógica do ábaco não funciona, porque não tem como pensar em uma quantidade negativa de discos, ou uma fração de um disco. A própria lógica física da ideia central do algoritmo limita seu funcionamento a vetores com números inteiros positivos. 

Claro, podemos pensar em algumas alternativas de gambiarra para adaptar o código para contornar essas limitações. Por exemplo, ao lidar com números negativos, podemos ter um número que soma o maior número negativo de forma a ele ficar positivo, ordena pelo Gravity Sort e então subtrai esse mesmo valor que foi somado para termos os valores originais. Sempre há um jeito de contornar limitações específicas.

Se for executado em hardware especializado, há garantia de que tenha complexidade $$O(n)$$, onde $$n$$ é o número de elementos do vetor. No exemplo, seria $$n = 5$$. Caso contrário, a implementação em software tem complexidade $$O(s)$$, onde $$s$$ é a soma de todos os elementos inteiros do vetor. No exemplo, seria $$s = 5 + 4 + 3 + 2 + 1 = 15.$$

O uso de memória, porém, é $$O(n^2)$$. Um ponto curioso de sua complexidade é que no seu pior caso ele, apesar da complexidade linear, consegue ser mais rápido que $$O(n log n)$$, de acordo com demonstrações de desempenho. Isso é possível porque o Gravity Sort explora a estrutura de lidar sempre com inteiros positivos. 

Pensando em software, a implementação do algoritmo em si tem uma questão: ok, a ideia parece interessante, mas como fazer isso dado um vetor na entrada da função?

De acordo com a [Wikipédia](https://en.wikipedia.org/wiki/Bead_sort#Implementation), podemos pensar em uma lista em Python com uma sequência de inteiros. A função retorna uma nova lista (ao invés de transmutar na própria lista de entrada), embora seja possível para uma operação *inplace*.

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