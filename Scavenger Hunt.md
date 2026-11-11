# Scavenger Hunt

> Categoria: Web Exploitation
>
> Autor: madStacks

[![image.png](https://i.postimg.cc/MTVXy5FY/image.png)](https://postimg.cc/474JG6ZK)

## Introdução

Este CTF está disponível no site CyLab, classificado como Web Exploitation e de dificuldade Fácil.

Seu enunciado pode ser traduzido para:

> " Há algumas informações escondidas por este site. Você consegue encontrar? "

Logo em seguida, um botão para lançar a instância, para informações adicionais e para acessar o site dito no enunciado:

[![image.png](https://i.postimg.cc/wBhd2r93/image.png)](https://postimg.cc/yJY5Yvgz)

## Análise inicial

Ao clicarmos na opção What, temos o que foi usado para fazer o site (HTML, CSS, JavaScript):

[![image.png](https://i.postimg.cc/KjYSZvBT/image.png)](https://postimg.cc/wynb2zWx)

Vamos dar uma olhada no código fonte da página e verificar as informações presentes:

[![image.png](https://i.postimg.cc/ryv26czR/image.png)](https://postimg.cc/6TLmRkrB)

No código fonte, temos algumas informações importantes. Começando pelos links disponibilizados:

- mycss.css
- myjs.js

E também, uma mensagem que informa a primeira parte da flag:

## Parte 1
> <!-- Here's the first part of the flag: academy{t -->

Instintivamente, percebemos que esse desafio consiste em procurar partes separadas da flag e juntá-las depois.
Isso é característico de desafios do tipo OSINT, e explica o título do desafio "Scavenger Hunt", traduzido, "Caça ao tesouro".

Agora, vamos abrir os links e procurar pelas partes restantes da flag.
Entrando no link que mostra o código CSS utilizado na página:

[![image.png](https://i.postimg.cc/FsBdXY0N/image.png)](https://postimg.cc/VdXLjL7V)

No final da página, uma mensagem que nos dá a parte 2 da flag:

## Parte 2
> /* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */

Entrando agora no link que mostra o código em JavaScript do site:

[![image.png](https://i.postimg.cc/fRYwqyKc/image.png)](https://postimg.cc/tsCQYX8J)

A mensagem no final do código pode ser traduzida para:

> " Como posso impedir o Google de indexar meu site? "

Isso é uma pista importante, e diz sobre uma modificação que pode ser feita na URL da página para mostrar páginas não listadas em uma pesquisa no navegador.
Essa modificação é "robots.txt". Isso acontece porque o arquivo robots.txt contém instruções para bots em mecanismos de busca,
restringindo quais sites eles podem ou não acessar, utilizado para evitar sobrecarga nos servidores.
Ao digitar "/robots.txt" no final da URL do site da instância, somos redirecionados para uma página contendo outra parte da flag:

[![image.png](https://i.postimg.cc/wv4yxMnB/image.png)](https://postimg.cc/xJHTtffr)

## Parte 3
> Part 3: t_0f_pl4c

E analisando a mensagem da página: 

> I think this is an apache server... can you Access the next flag?
>
> Eu acho que esse é um servidor apache... você consegue Acessar a próxima flag?

A mensagem fala sobre um servidor apache, e com um detalhe importante: Access tem a letra A maiúscula.
Isso é proposital, e indica que é necessário conceder acesso a este servidor.
O próximo passo é substituir "robots.txt" por ".htaccess" na URL da página, obtendo mais uma parte da flag:

[![image.png](https://i.postimg.cc/7Y96qf7L/image.png)](https://postimg.cc/fJ3ZKW84)

## Parte 4
> Part 4: 3s_2_lO0k

E, novamente, mais uma mensagem que nos levará a parte final da flag:

> I love making websites on my Mac, I can Store a lot of information there.
>
> Eu amo fazer websites no meu Mac, eu posso Armazenar um monte de informação lá.

O autor fala sobre fazer websites no Mac, e com um detalhe sobre a letra maiúscula em Store.
Isso nos leva ao arquivo do tipo .DS_Store, que é utilizado no macOS para armazenar informações visuais.
Portanto, ao trocar ".htaccess", da página atual, por ".DS_Store", conseguimos a última parte da flag!

[![image.png](https://i.postimg.cc/zXVMGQHW/image.png)](https://postimg.cc/1f1MWJH5)

## Parte 5
> Congrats! You've completed the scavenger hunt! Part 5: _2b9c61f}

## Conclusão
Por fim, resta juntar todas as partes da flag para formar a flag que deve ser escrita no site CyLab para resolver o desafio.
No final, obtemos a flag:

> academy{th4ts_4_l0t_0f_pl4c3s_2_lO0k_2b9c61f}
