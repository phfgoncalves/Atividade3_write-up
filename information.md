# information

> Categoria: Forensics
>
> Autor: susie

[![image.png](https://i.postimg.cc/0y3xWxYY/image.png)](https://postimg.cc/NK1WF3PF)

## Introdução

Este CTF no site CyLab é classificado como Fácil na categoria de Forensics (Forense). A tradução do seu enunciado é:

> Arquivos sempre podem ser mudados de um jeito secreto. Você consegue encontrar a flag?

E junto do enunciado, um arquivo jpg: 

[![cat-(1).jpg](https://i.postimg.cc/Rh3LT74L/cat-(1).jpg)](https://postimg.cc/YLHFrm4v)

Vamos desconsiderar as dicas disponibilizadas neste desafio.


## Análise inicial

Em se tratando de um desafio de análise forense, é esperado encontrar metadados escondidos na imagem a fim de chegar até a flag. 
Para tal, vamos utilizar o site AperiSolve, uma ferramenta para analisar imagens.

- https://www.aperisolve.com/

Ao fazer o upload do arquivo da questão cat.jpg e analisar o arquivo, obtemos várias informações da imagem, alguns ajustes de contraste e cor, tamanho, etc.
Porém, o que nos interessa aqui são os metadados da imagem, que ficam na sessão

> Exiftool

[![image.png](https://i.postimg.cc/YqRQmD1R/image.png)](https://postimg.cc/PPLCg4Vv)

Mais especificamente, o conteúdo em "License" que parece esconder uma mensagem criptografada.

Como não sabemos o tipo de criptografia utilizado, recorremos ao site dCode e sua função Cipher Identifier, para identificar a criptografia utilizada:

- https://www.dcode.fr/cipher-identifier

[![image.png](https://i.postimg.cc/QdWxrHx6/image.png)](https://postimg.cc/LJ2Mt4Pf)

Ao copiar o conteúdo no site dCode, ele identifica que a mensagem está em Base64, portanto, podemos clicar na opção que foi identificada para decifrar a mensagem:

[![image.png](https://i.postimg.cc/fbD4gL3J/image.png)](https://postimg.cc/FYWnYhV4)

Isso nos dá a flag diretamente em texto claro.

## Conclusão

Para solucionar o desafio, só nos resta copiar a flag obtida pelo site dCode no CyLab e finalizar a questão.
Em desafios de Forense, é esperado encontrar metadados ou informações importantes na imagem.
Neste caso, a flag estava escondida na imagem e protegida por uma criptografia. Ao identificar o tipo de criptografia, bastou decodificar a mensagem e obter a flag.
