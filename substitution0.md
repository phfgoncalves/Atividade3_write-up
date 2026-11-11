# substitution0

> Categoria: Cryptography
>
> Autor: Will Hong

[![image.png](https://i.postimg.cc/hvrMvDDH/image.png)](https://postimg.cc/648C1NG0)

## Introdução

substitution0 é um desafio de CTF da plataforma CyLab classificado como dificuldade Média nos desafios de Cryptography (Criptografia).

Seu enunciado pode ser traduzido para:

> Uma mensagem chegou, mas parece estar toda embaralhada. Felizmente, parece que tem a chave no começo. Você consegue decifrar este cifra de substituição? Baixe a mensagem aqui

E podemos baixar o arquivo da questão clicando no "here" ao final do enunciado, que é um arquivo .txt:

[![image.png](https://i.postimg.cc/BbXtLN4s/image.png)](https://postimg.cc/fSQM1cVg)

A mensagem está toda criptografada, como esperado, mas precisamos saber qual criptografia foi utilizada para formar essa mensagem,
tendo em mente que a chave está no começo do arquivo (ou seja, o método de criptografia utiliza uma chave).
Nesse caso, podemos copiar e colar a mensagem no site dCode, com sua função Cipher Identifier para identificar o código utilizado na mensagem.

- https://www.dcode.fr/cipher-identifier

[![image.png](https://i.postimg.cc/TwyphCR6/image.png)](https://postimg.cc/Kk2ZH7kq)

E ao copiar o conteúdo do arquivo e clicar em Analyze, o site mostra as criptografias mais prováveis usadas na mensagem:

[![image.png](https://i.postimg.cc/3xgjxrtv/image.png)](https://postimg.cc/TK35kxMd)

Agora, para decidir qual cifra foi utilizada na questão, vamos relacionar o título do desafio com os códigos mais prováveis
> substitution0 -> Mono-alphabetic Substitution
> 
> substitution0 -> Substitution Cipher

Temos 2 cifras possíveis. Vamos utilizar a Mono-alphabetic Substitution, porque é a cifra mais provável de acordo com o dCode Cipher Identifier.

Copiamos o texto encriptado, e informamos a chave no local correto para decodificar a mensagem:

[![image.png](https://i.postimg.cc/yxy3cjbG/image.png)](https://postimg.cc/MfXG87x0)

# Conclusão

Com isso, obtemos toda a mensagem em texto claro, e a flag ao final da mensagem:

> academy{5UB5717U710N_3V0LU710N_4FBD1EB7}

Nesse caso, basta copiar a flag e colar no site do CyLab para resolver o desafio substitution0.
Em desafios de Crypto, é necessário encontrar qual criptografia foi utilizada na mensagem.
Deve-se avaliar se precisa de uma chave para decodificar, como nessa questão, para obter a flag.
