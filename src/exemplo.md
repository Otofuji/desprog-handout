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

    {IMAGEM ÁBACO – "SERÁ PRODUZIDA POSTERIORMENTE"}

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

    {ANIMAÇÃO ÁBACO – "SERÁ PRODUZIDA POSTERIORMENTE"}

Aqui outra animação que representa o algoritmo para entradas maiores.

    {ANIMAÇÃO ALGORITMO – "SERÁ PRODUZIDA POSTERIORMENTE"}

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

Para nossa análise didática, podemos simplificar essa afirmação valendo-se das regras de simplificação do Hashimoto e considerar, grosso modo, que o Gravity Sort tem complexidade $$O(n)$$ para todos os casos.

O uso de memória, porém, é $$O(n^2)$$. Um ponto curioso de sua complexidade é que no seu pior caso ele, apesar da complexidade linear, consegue ser mais rápido que $$O(n log n)$$, de acordo com demonstrações de desempenho. Isso é possível porque o Gravity Sort explora a estrutura de lidar sempre com inteiros positivos. 

Pensando em software, a implementação do algoritmo em si tem uma questão: ok, a ideia parece interessante, mas como fazer isso dado um vetor na entrada da função?

>PERGUNTA: Proponha uma estrutura de dados que possa ser usada dentro da função para alocar os inteiros do vetor a ser ordenado que permita a implementação dessa estrutura de ábaco.

**Dica:** pense em termos de vetores, matrizes, lista ligada etc., e então em uma forma (alto nível, sem implementação em código propriamente dita) de que essa estrutura possa ser usada para implementar em software o Gravity Sort.

***

Não continue até ser validado.




###

Fim do handout
--------------------

>Fim do handout

Fim do handout

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus tincidunt, eros porta scelerisque efficitur, nisi dolor eleifend eros, in dictum sapien ex id sapien. Fusce pharetra efficitur mattis. Proin vel justo lacus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Cras porta ac tellus quis congue. In bibendum mauris sit amet augue tempor, eget rutrum velit tempus. Mauris pharetra laoreet condimentum. Nam nec dignissim magna. Nulla vitae lectus et eros feugiat euismod vel eget dui. Vestibulum venenatis condimentum luctus. Suspendisse commodo ipsum et nisl porttitor tincidunt. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Sed nec accumsan ante, sit amet condimentum ante. Curabitur ultrices felis at nibh auctor, a finibus dui hendrerit.

In lectus sem, iaculis vel elementum ac, iaculis quis leo. Morbi convallis ultrices interdum. Cras congue, justo et tristique tempor, lacus purus vestibulum enim, eu congue augue quam in magna. Vivamus condimentum dignissim nisl et pellentesque. Nulla ut suscipit mauris. Maecenas interdum auctor porttitor. Donec laoreet nulla eget ex gravida venenatis. Curabitur pellentesque elit magna, et efficitur dolor pharetra pellentesque. Morbi diam sapien, volutpat ornare turpis ut, vestibulum efficitur orci. Nulla facilisi. Donec ut congue orci. Morbi sed ullamcorper est. Nam scelerisque pellentesque nisl, eu tincidunt nibh pharetra a. Nulla a luctus augue. Sed pulvinar sapien at enim consectetur fringilla. Aenean ac purus ullamcorper nibh tincidunt pharetra.

Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Nullam lobortis enim a metus elementum, aliquet volutpat metus efficitur. Quisque elementum et elit vel fringilla. Mauris viverra accumsan felis, sed eleifend augue hendrerit vel. Ut aliquam tellus et neque mollis accumsan. In nec eros sit amet justo ornare accumsan. Sed vitae metus convallis, facilisis risus id, lobortis erat. In interdum pellentesque dolor, a tempor neque molestie sit amet. Pellentesque elementum varius metus in tristique. Sed non metus commodo, vestibulum diam id, porta felis. Proin ut justo id nulla sagittis auctor. Suspendisse eleifend efficitur vehicula. Donec placerat ornare libero sed sagittis. In a augue est. Integer blandit, augue eu rutrum ultrices, est lacus elementum urna, ut posuere erat nulla imperdiet tellus. Nam luctus laoreet dui, non aliquam felis tincidunt eu.

In eu consequat mauris. In ultrices neque non velit facilisis pellentesque. Pellentesque at lobortis tortor. Sed porta vulputate volutpat. Nam eu blandit sapien. Vivamus tempus, turpis in interdum scelerisque, dui nunc finibus lacus, ut consectetur lectus leo in felis. Nullam massa turpis, dignissim vitae tortor a, facilisis laoreet libero. Quisque tincidunt vehicula lectus.

Nam facilisis pharetra enim, vitae cursus tortor laoreet id. Duis et vulputate diam. Mauris at dignissim libero. Nulla finibus nulla sit amet rutrum lobortis. Morbi dignissim dignissim leo nec dapibus. Vivamus tempor malesuada mi a ultrices. Proin in rhoncus quam. Praesent sed congue magna. Morbi ac fermentum purus. Morbi vitae justo a arcu vestibulum tristique. Integer lacinia justo sit amet mattis suscipit. Nunc tempor nulla et est commodo lobortis vitae vitae felis. Maecenas at lacus ut turpis finibus efficitur id non velit.

Nam sapien sem, consequat at tincidunt ac, scelerisque vitae ipsum. Duis dictum nisi ac tellus egestas convallis. Proin id tincidunt nibh, eget sollicitudin arcu. Morbi auctor sollicitudin nibh nec congue. Interdum et malesuada fames ac ante ipsum primis in faucibus. Morbi purus ligula, finibus nec enim eu, aliquam auctor ante. Nullam volutpat vitae ipsum a aliquet. Vivamus nec arcu lacus.

Donec et eros tempor, maximus magna sit amet, pulvinar augue. Duis malesuada nibh vitae convallis luctus. Mauris accumsan tellus ut lacus semper dignissim. In mattis ante id hendrerit viverra. Phasellus sed purus lectus. Duis sit amet convallis velit, a consequat ipsum. Aliquam vel lacus neque. In rhoncus ultricies viverra. Pellentesque egestas egestas massa pellentesque mattis. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Morbi luctus justo tortor, in eleifend enim laoreet sed. Etiam in velit vitae massa bibendum feugiat. Duis ut mi augue. Donec felis leo, fringilla ac nulla vel, mattis vehicula magna. Curabitur et ultricies augue. Quisque ultricies erat et mollis cursus.

Aenean eget tellus interdum, viverra magna vel, egestas velit. Ut sem mauris, scelerisque vitae laoreet a, rhoncus eu diam. Sed iaculis, neque sed tincidunt eleifend, metus odio dictum turpis, sed ullamcorper augue nisi sit amet libero. Aliquam aliquet eu purus ac posuere. Nam mi purus, mollis et sapien a, accumsan ultrices urna. Praesent et venenatis massa. Donec enim ipsum, consectetur vehicula tortor vitae, aliquam condimentum tortor. Ut imperdiet tempus arcu vel rutrum. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. In auctor pellentesque lacus a mattis. Donec ultrices diam ut dui luctus dapibus ut maximus orci. Morbi molestie lacus justo, ut porta libero rutrum et. Curabitur commodo commodo erat sit amet porttitor. Mauris ullamcorper sit amet felis vitae placerat. Aliquam sit amet lectus a turpis volutpat hendrerit id sit amet ante.

Praesent imperdiet nulla arcu, eu semper risus consequat at. Ut lacus nulla, lacinia quis metus quis, pretium accumsan arcu. Aliquam erat volutpat. Aliquam mattis porta vulputate. Morbi viverra nibh ut libero blandit, sit amet dignissim ipsum tristique. Integer congue est eget condimentum venenatis. Proin at pharetra eros. Nunc ac suscipit augue. Fusce et convallis ante, et feugiat mi. Pellentesque rhoncus quam semper felis posuere tempus. Donec quis ipsum mauris. Donec maximus, dolor nec dapibus viverra, justo nunc luctus ex, vitae volutpat nibh massa eget justo.

Nunc dictum lorem id luctus ornare. Sed commodo suscipit neque, et molestie neque faucibus id. Suspendisse aliquet ex dolor, in consectetur mi aliquet vitae. Ut at vehicula velit. Etiam mollis, nunc a consectetur vulputate, tortor diam lacinia tellus, in elementum enim risus at ligula. In nec erat at enim malesuada lobortis vitae at libero. In mollis non mauris sit amet faucibus. Morbi at lobortis massa. In accumsan a nisl et imperdiet. Mauris vel magna a lacus sollicitudin tristique. Donec semper ante quis nulla dignissim porta. Suspendisse iaculis interdum ipsum, in vulputate nisl lobortis eu. Etiam porta risus vitae nisl ullamcorper ultrices. Nunc felis lectus, malesuada consequat mollis ac, sollicitudin a urna. Donec risus quam, fringilla sit amet accumsan et, imperdiet at erat. Nullam gravida posuere arcu nec ultrices.

Donec ultrices, quam sed semper laoreet, neque elit dictum risus, et rutrum est massa ac mi. Aenean condimentum ac turpis eget varius. Integer sed ante quis lorem pellentesque placerat. Nulla pretium felis lacus, a scelerisque lectus vehicula ut. Nullam convallis mollis leo eget ultrices. Phasellus vulputate interdum pellentesque. Praesent vel turpis ultrices, suscipit neque eu, lacinia lorem. Fusce egestas bibendum egestas. Aliquam porta ornare egestas. Phasellus vitae lacus magna. Morbi suscipit hendrerit odio eget tincidunt. Duis cursus a mauris a faucibus.

Praesent mattis turpis purus, ut dapibus libero imperdiet pretium. Aenean at eros est. Integer tincidunt est blandit tincidunt luctus. Curabitur augue dui, cursus in tellus nec, euismod mollis risus. Proin maximus pellentesque est non finibus. Quisque dictum, nisl varius condimentum auctor, tortor nisi lobortis eros, ut tincidunt velit velit pretium tellus. Suspendisse ornare enim ut nisl accumsan, in luctus risus vehicula. Nullam lobortis nisi lectus, nec condimentum sem mollis in. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus dolor enim, vestibulum id mollis sed, ullamcorper sed nisl. Donec cursus, enim sit amet convallis iaculis, ex neque convallis tortor, in tincidunt dui neque ac lacus. Cras vitae turpis viverra, ultrices sem iaculis, congue odio. Maecenas ultricies velit non orci gravida bibendum. Maecenas egestas vestibulum tempus.

Mauris pellentesque felis ac purus semper, lacinia imperdiet nibh sodales. Sed id semper sem. Sed bibendum aliquam tristique. Quisque vitae dolor ut leo elementum molestie a vel erat. Nulla eget mi augue. Nullam euismod libero sit amet dolor bibendum finibus. Aliquam erat volutpat. Nulla lacinia, lectus in ornare venenatis, lectus neque aliquet dolor, vitae pellentesque velit nisi ullamcorper turpis. Nam dignissim ipsum hendrerit blandit finibus. Vestibulum eu elit eu lectus posuere sagittis tincidunt nec lacus. Duis sed feugiat arcu, sit amet suscipit velit. Nullam in tellus quis massa aliquam lobortis id a purus. Phasellus a eros at velit ultricies accumsan. Maecenas urna odio, eleifend venenatis faucibus in, ultricies at lacus. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.

Quisque velit risus, faucibus id elit vel, consequat volutpat quam. Nullam maximus justo quis enim pellentesque, ut consectetur augue convallis. Quisque porta congue erat, in commodo nisi feugiat ut. Nam erat tellus, ultrices vulputate tempus ut, fermentum eu sapien. Pellentesque vehicula pellentesque sapien in egestas. Fusce id faucibus elit. Curabitur nec lacus eu mauris lacinia ultricies. Sed eget nisl sit amet odio mollis ullamcorper. Pellentesque in ipsum enim.

Duis quis enim sagittis purus imperdiet aliquam at nec dolor. In laoreet lacus id nisl gravida semper. In malesuada molestie sapien, a gravida justo vestibulum nec. Suspendisse auctor dui lorem, vitae consequat ex cursus eget. Quisque aliquet lorem sed enim dignissim, sed dignissim justo efficitur. Sed ornare ullamcorper lacus, in hendrerit lectus hendrerit nec. Duis interdum est vel metus iaculis, vel viverra nunc sodales. Nulla at tincidunt tellus, id efficitur urna.

In vulputate eros ligula, vitae faucibus erat iaculis vel. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec gravida fringilla nunc, viverra euismod massa malesuada vitae. Sed vitae rhoncus lorem. Quisque maximus, lectus quis ultricies mattis, tellus tortor rutrum enim, ac mattis mauris nunc nec dui. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Curabitur id lectus tempor, vehicula tellus at, sodales dolor. Nunc faucibus convallis nibh eu volutpat. In hac habitasse platea dictumst. Nullam vel sodales sem. Donec consequat arcu vitae augue tristique tincidunt. Ut maximus commodo metus vitae luctus. Donec in euismod enim, in eleifend orci. Integer id tortor rhoncus, iaculis arcu sit amet, gravida justo.

Pellentesque condimentum lacinia urna vitae egestas. Maecenas vitae justo pharetra, maximus neque ut, luctus nulla. Pellentesque justo odio, egestas a semper vitae, pharetra et lacus. Morbi auctor eros a augue auctor, quis porta odio rhoncus. Aliquam finibus ipsum id risus finibus sodales. Ut in viverra velit. Ut eget posuere magna, in pellentesque magna. Vestibulum iaculis viverra rhoncus. Proin molestie rhoncus condimentum. Aenean sit amet quam sem. Praesent tristique massa eget luctus dignissim.

Mauris molestie lorem ut tellus fermentum hendrerit. Donec laoreet gravida quam in scelerisque. Praesent ex ante, scelerisque vel pharetra non, lacinia ut orci. Curabitur convallis rutrum massa, sit amet pulvinar arcu commodo at. Etiam rhoncus sit amet nibh non hendrerit. Pellentesque eget nisi ut ex congue vestibulum ut et nisi. Nam finibus in tortor sit amet rutrum. Aenean nulla est, fermentum rhoncus tortor vel, pharetra aliquam mauris. Nunc vestibulum ligula justo, eu condimentum lacus eleifend et. Pellentesque et ornare tellus.

Curabitur vitae ipsum erat. Quisque congue commodo mi, sit amet tristique massa feugiat sit amet. Pellentesque commodo gravida mauris eleifend ullamcorper. Integer molestie quis risus quis posuere. Phasellus tempus facilisis lacus, a tempus mauris consectetur sed. Morbi tortor neque, sagittis sed nulla id, tempor cursus sem. Morbi suscipit, mauris id convallis aliquam, justo neque dignissim nisl, aliquam facilisis sem orci a lorem. Integer ac erat eu turpis finibus dapibus. Nunc fermentum leo sapien, id imperdiet elit scelerisque in. Nulla sed nibh ex. In pulvinar magna sit amet justo luctus, vel cursus ligula faucibus. Nam ullamcorper a sem ac laoreet. Maecenas tincidunt fringilla erat sed bibendum.

Integer id turpis pretium, maximus orci quis, pretium elit. Nunc vel purus nunc. Nunc vel urna dolor. Donec sed efficitur erat. Vivamus tellus purus, imperdiet quis gravida a, ultrices in tellus. Aliquam malesuada urna vitae mollis pharetra. Aliquam erat volutpat. Pellentesque tempor tempus bibendum. Morbi sed volutpat erat.

Nunc maximus libero in egestas efficitur. Vestibulum non ultricies ante. Cras mattis diam id pulvinar sagittis. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Morbi mauris sapien, porta eget augue sit amet, consequat porta arcu. Mauris a vulputate mi, a rutrum lorem. Nunc sed tellus posuere, laoreet lorem sed, mollis lacus. Suspendisse sagittis varius mauris, sed mattis orci finibus ut. Vivamus ut lectus vulputate, gravida leo vitae, pharetra dui. Pellentesque consectetur, mi ut condimentum mollis, augue magna sodales odio, vitae finibus ligula eros non lectus.

Aenean condimentum aliquet enim, ut pharetra velit aliquam accumsan. Duis et nibh bibendum, mollis tortor at, auctor nisi. Suspendisse dolor leo, faucibus eget euismod non, rutrum eget metus. Curabitur aliquam blandit aliquet. Nam dapibus erat vel pellentesque ultrices. Donec vitae turpis vel neque consectetur maximus. Aliquam erat volutpat. Duis fringilla ex sit amet mauris laoreet euismod. Nulla condimentum posuere quam, at luctus ipsum maximus vel. Duis sit amet pulvinar elit, vel ullamcorper quam. Donec sed leo vel nisi aliquet interdum eget eget nibh. Vivamus consequat bibendum efficitur. Duis bibendum, ex sed sodales consectetur, elit tellus maximus turpis, ac mattis ex dui elementum nisl. Phasellus porttitor dictum ullamcorper. Aenean leo nunc, tempus nec leo quis, egestas facilisis sapien. Nullam augue dolor, porta eget vehicula vel, maximus imperdiet ante.

Sed fermentum placerat tempor. Vivamus at varius ex. Nullam turpis leo, imperdiet vitae dapibus vel, mollis ac sem. Suspendisse turpis sem, imperdiet nec pharetra a, varius vel tortor. Morbi odio metus, varius ac rhoncus at, dignissim mollis libero. Curabitur id tortor sem. Quisque facilisis semper nulla, vitae efficitur lorem pretium eget. Proin et orci consequat, consectetur leo sit amet, imperdiet ipsum. Proin rutrum dolor ac lorem molestie, vitae vulputate ex varius. Integer tempor pellentesque nisl et cursus. Phasellus at lorem id velit viverra congue. Sed non tellus diam.

Sed felis dui, aliquet non purus eu, lobortis lacinia augue. Vivamus tincidunt quam semper hendrerit sollicitudin. Curabitur ante urna, ullamcorper a tellus eget, ultricies cursus odio. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. In vestibulum nulla tortor, quis lacinia justo tristique sed. Maecenas magna metus, tincidunt id semper at, feugiat accumsan neque. Vivamus suscipit, justo vel faucibus luctus, ex ex scelerisque ipsum, nec tempor elit tellus vel nibh. In posuere, est vitae convallis fringilla, libero velit fermentum tellus, aliquet placerat nulla turpis et velit. Nulla facilisi. Vivamus a faucibus massa. Proin vitae lacinia tellus, nec faucibus justo.

Integer commodo, sapien et rutrum tempor, dolor nisl aliquam tellus, ut lacinia dolor magna vitae lorem. Vivamus id massa justo. Donec at ante a purus varius molestie et in ex. Nam mi lacus, dapibus vel pulvinar sit amet, pharetra in nunc. Aliquam erat volutpat. Duis vulputate magna sit amet ipsum rhoncus, non eleifend nunc suscipit. Sed sodales aliquet purus vitae luctus. Pellentesque a interdum tortor. Pellentesque accumsan congue sem, vel sodales eros lacinia nec. Suspendisse tristique vel libero in sodales. Mauris tempor nibh vel lacus elementum viverra. Donec finibus, nunc in pulvinar placerat, dui arcu tincidunt ex, blandit aliquet tortor arcu vitae metus. Fusce nec orci ut mauris vulputate rhoncus non ut nunc. Fusce quis justo tristique, vestibulum augue sed, condimentum nulla. Ut nisi nibh, blandit sed ornare in, hendrerit id ipsum. Aliquam in sollicitudin odio.

Nullam ac dignissim purus, non bibendum nulla. Mauris a pretium ex. Pellentesque ut dolor mi. Vestibulum tincidunt volutpat ante, sit amet ullamcorper risus sagittis ac. Nunc est lectus, sagittis ac magna sollicitudin, vestibulum iaculis urna. Donec vehicula tempus libero a venenatis. Duis non tortor eleifend, finibus ante vitae, elementum ex. Sed eu aliquet dui. Fusce bibendum libero at mauris iaculis interdum. In tempus quam venenatis ipsum semper cursus. Donec egestas erat ipsum, vel imperdiet sem tristique et.

In cursus, turpis eu tempor vulputate, tellus mi consequat enim, sit amet hendrerit turpis mi ac justo. Aenean egestas ex nec augue convallis, a malesuada lectus efficitur. Sed neque ipsum, auctor nec viverra vestibulum, sodales vitae ligula. Nunc quis metus ac ligula tempor rhoncus. Mauris tincidunt congue sapien nec malesuada. Nullam sagittis scelerisque ipsum eu ultricies. Nulla venenatis massa at velit facilisis, sit amet egestas ligula luctus. Suspendisse non risus eu quam vehicula laoreet. Nunc sed condimentum arcu.

Ut pretium turpis urna. Interdum et malesuada fames ac ante ipsum primis in faucibus. Praesent placerat molestie diam, sed gravida justo maximus vitae. Donec nunc felis, interdum vitae elit non, molestie sagittis felis. Suspendisse potenti. Curabitur non justo magna. Nam et lacus viverra, porttitor lacus a, euismod diam. Praesent facilisis elit ac tincidunt fringilla. Nulla ac augue ut velit mattis porttitor sed a purus. Cras nec nisi at massa commodo tristique nec sit amet tortor. Fusce vitae ornare risus. Phasellus orci ante, blandit a ante mattis, semper tincidunt leo. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.

Nam sit amet leo sit amet orci consectetur finibus. Mauris eu auctor lorem, in ornare nibh. Donec sit amet metus fringilla, aliquam quam vel, pulvinar risus. Nulla ac ultricies nisl. Donec non felis nec nisi gravida vulputate eu sed ante. Nullam blandit magna ac fringilla interdum. Nunc finibus nisi nec iaculis tempus. Nullam quis tortor sit amet orci iaculis suscipit.

Duis tristique a nisl sed tincidunt. Nam egestas lacinia eros, vel lobortis lorem tempus non. In ornare massa quis odio egestas sodales. Mauris non leo suscipit, vulputate nisl quis, gravida massa. Integer ut ornare ex. In non tempor erat. Nulla facilisi. Mauris placerat lorem at nulla efficitur imperdiet. Aenean sapien eros, commodo at sem sed, hendrerit pulvinar tortor. Donec pharetra tellus nulla, quis hendrerit nulla dictum non. Aliquam erat volutpat. Aliquam diam sem, bibendum at turpis ac, vehicula placerat nibh. Nunc fermentum quis lorem sed pellentesque.

Praesent pretium massa non metus accumsan, in tempor sapien bibendum. Nullam varius ex id ante volutpat, in pretium dolor aliquet. Integer dui purus, luctus in accumsan sit amet, vehicula non risus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Aenean viverra augue eu arcu pretium eleifend. Quisque quis odio arcu. Integer venenatis sollicitudin lorem, sit amet euismod tellus laoreet ac. Etiam feugiat dictum sapien nec venenatis.

Sed vel ligula mauris. Ut faucibus justo quis tellus posuere scelerisque. Pellentesque ipsum massa, luctus eu dapibus sit amet, pharetra id augue. Fusce eu tortor vitae tellus luctus aliquet. Integer quis tincidunt metus. Nam quam risus, suscipit vitae malesuada ut, consequat a turpis. Vestibulum at sapien convallis, malesuada arcu non, facilisis dui. Vestibulum lobortis pharetra eleifend. Curabitur porta gravida volutpat. Integer congue vulputate tortor at viverra. Ut hendrerit mattis nunc. Etiam eget bibendum nibh, ac mollis eros.




###

Exemplo Hashimoto
--------------------

>Exemplo. Uso interno.

Em texto normal, você pode usar *itálico*, **negrito**, `código` e `>comando`.
Como você pode ver nesse exemplo, o modo de código é para ser usado em texto de
código-fonte. Quando você tenta escrever texto normal, efeitos estranhos podem
acontecer, como essa cor diferente no "o" com acento agudo.

Você também pode usar $$\LaTeX$$, se souber. Tanto no meio ($$\sum^n_{i=1}i$$)
de parágrafos, quanto em parágrafos próprios centralizados:

$$$\sum^n_{i=1}i.$$$

Adicionalmente, também pode criar

* listas

* não-ordenadas,

assim como

1. listas

2. ordenadas.

Finalmente, também pode criar

    print('código em parágrafo destacado,')

assim como

    >PREVIOUSLY, ON INSPER ENGINEERING…


Nesses dois casos, espaços em branco e quebras de linha serão respeitados.


Exemplo de subtítulo
--------------------

A notação para criar [um link](https://www.insper.edu.br/) é bem simples.

A notação para criar

![uma imagem](exemplo.png)

é bem parecida. Espera-se que todas as imagens estejam na pasta *img*.