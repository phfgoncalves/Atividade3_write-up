# First Find

> Categoria: General Skills
>
> Autor: LT 'syreal' Jones

[![image.png](https://i.postimg.cc/nzPZ9J31/image.png)](https://postimg.cc/zbK449ZL)

## Introdução

Este desafio CTF no CyLab é classificado na categoria Fácil dentre os desafios de General Skills ou Misc. Seu enunciado é direto:

> " Descompacte essa pasta e encontre o arquivo nomeado 'uber-secret.txt' "

Ao baixar a pasta e extrair tudo, obtemos: 

[![image.png](https://i.postimg.cc/wTWP6VbG/image.png)](https://postimg.cc/6yvzcdKr)

E ao entrar na pasta files, mais pastas e arquivos aleatórios:

[![image.png](https://i.postimg.cc/SRR6VW7b/image.png)](https://postimg.cc/xNrN1N46)

## Análise inicial

A partir deste ponto, e com base no enunciado da questão, a flag está no arquivo uber-secret.txt, que está em algum diretório específico no meio de várias pastas
contendo arquivos aleatórios diferentes do arquivo que procuramos. Portanto, o próximo passo é procurar em cada pasta o arquivo necessário, com cuidado para não se perder ou esquecer de algum diretório. Um bom mecanismo para utilizar em situações de busca como essa é a busca aprofundada, que consiste em procurar em uma pasta de cada vez, até chegar na última pasta do diretório, e depois voltar para o início.

## Conclusão

[![image.png](https://i.postimg.cc/y6034pxM/image.png)](https://postimg.cc/K4v8tNnf)

O arquivo uber-secret.txt está nesta sequência de diretórios:
> files, adequate_books, more_books, .secret, deeper_secrets, deepest_secrets, uber-secret.txt

[![image.png](https://i.postimg.cc/prVHSdpp/image.png)](https://postimg.cc/wyrZyg5p)

Ao abrir o arquivo, a única mensagem é a flag em texto claro, restando apenas copiá-la e colar no site do CyLab para resolver o desafio.
