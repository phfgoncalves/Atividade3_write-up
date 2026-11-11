# crackme-py

> Categoria: Reverse Engineering
> 
> Autor: syreal

[![image.png](https://i.postimg.cc/263LN0sF/image.png)](https://postimg.cc/HcDkQ9sV)

# Introdução

Este CTF de Engenharia Reversa é de dificuldade Média no site CyLab. O desafio consiste em baixar o arquivo crackme_gen.py fornecido na questão,
abrir utilizando o VSCode e analisar o que o código em Python faz. Não há nenhum enunciado na questão, portanto, a flag está dentro do arquivo.

Página do desafio: https://learn.cylabacademy.org/library/175?page=1&search=crackme

# Análise Inicial

Como não há enunciado na questão, vamos partir direto para a análise do código em Python a seguir:

[![image.png](https://i.postimg.cc/Gm1DTJyS/image.png)](https://postimg.cc/QH0CR7Sp)

Lendo os comentários do código, temos a tradução:
> " Esconder esse número realmente importante em um pedaço obscuro de código é brilhante!
>   E está criptografado!
>   Queremos que nosso maior cliente saiba que suas informações estão seguras conosco. "

Ou seja, há um número escondido no código, e este número está criptografado. Já obtemos uma informação importante sobre a questão.

Prosseguindo com a análise, temos a declaração bezos_cc_secret = "24256>JL`>0c0Abc?FE02a_53e7fe7af5gN",
agora o valor dessa variável é essa string, provavelmente criptografa, mas ainda não sabemos qual criptografia foi utilizada.

Temos então a função decode_secret (decodificar segredo), cujo comentário é:
> " """ROT47 decode
>
>    NOTE: encode and decode are the same operation in the ROT cipher family.
>    """ "

Agora sabemos que foi utilizado ROT47 para criptografar o segredo que vimos anteriormente.

Seguindo com a análise do código, temos a função choose_greatest, que apenas analisa 2 valores de entrada do usuário e compara qual é maior.
Essa função não tem relação com a flag.

# Conclusão

Agora sabemos qual a string corresponde ao "segredo" dito no código, e qual criptografia foi utilizada.
Pesquisamos então por "ROT47 decoder", para conseguir decodificar a string e obter a flag.
Vamos utilizar o site dCode:

[![image.png](https://i.postimg.cc/wMLPx8ZN/image.png)](https://postimg.cc/JH7KKg17)

Copiando e colando a string "24256>JL`>0c0Abc?FE02a_53e7fe7af5gN" no site, obtemos diretamente a flag:

[![image.png](https://i.postimg.cc/wMp2Vt4z/image.png)](https://postimg.cc/WF50p4PY)

Ao copiar a flag academy{1m_4_p34nut_a20db6f76f27d8} e colar no desafio do CyLab, conseguimos resolver a questão.
