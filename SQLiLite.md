# SQLiLite

> Categoria: Web Exploitation
>
> Autor: Mubarak Mikail

[![image.png](https://i.postimg.cc/C13k0dWW/image.png)](https://postimg.cc/8JbjBkkH)

## Introdução

SQLiLite é um CTF do site CyLab, na categoria de Web Exploitation. Esse desafio é classificado como Médio, e seu enunciado é simples e pode ser traduzido para:

> " Você consegue logar nesse website? "

Logo após, é dito que precisamos lançar uma instância para aparecer mais detalhes e acessar o website onde conseguiremos a flag.

## Análise Inicial

Este é o site fornecido ao lançar a instância: 

[![image.png](https://i.postimg.cc/dt9SVK42/image.png)](https://postimg.cc/hff02NFv)

Nosso objetivo é logar no site, então vamos digitar um username e uma senha genéricos para ver o resultado.
Ao tentar admin para username e senha, o site redireciona para uma página informando que o login falhou:

[![image.png](https://i.postimg.cc/d3srWgdx/image.png)](https://postimg.cc/k6H2G1TQ)

Uma informação bastante importante nessa página, é a query utilizada para buscar as informações no banco de dados do site:

> SQL query: SELECT * FROM users WHERE name='admin' AND password='admin'

Portanto, aqui entramos no tema que dá título à questão, "SQLiLite". SQL é uma linguagem utilizada em banco de dados, e funciona com uma query que busca
informações necessárias. Nesse caso, busca nomes e senhas registrados em 'users'.

E ao saber a query exata no processo de login, podemos digitar um comando diretamente no campo de username ou senha para que o banco de dados execute o comando SQL.
Isso é uma vulnerabilidade Web conhecida (SQL Injection), que consiste na injeção de comandos SQL diretamente pelo website.

Ao analisar o formato da query, é possível formular um comando para burlar a busca de nomes e senhas no banco de dados e simplesmente aceitar o login.
Isso pode ser feito ao digitar no campo de senha:

> ' OR '1'='1

Já que ' 1 = 1 ' é sempre verdadeiro, mesmo se a senha digitada por incorreta, um valor falso OU um valor verdadeiro, retorna verdadeiro, resultado no login no site:

[![image.png](https://i.postimg.cc/c4D2cSYV/image.png)](https://postimg.cc/GHyXc6XQ)

Agora estamos logados, mas a flag não foi revelada ainda.
Há uma mensagem que diz:

> Logado! Mas você consegue ver a flag, está em texto claro.

Portanto, vamos inspecionar a página e procurar pela flag.
Ao olhar o corpo da página, conseguimos a flag:

[![image.png](https://i.postimg.cc/VvvBf365/image.png)](https://postimg.cc/H8G73vbC)

> academy{L00k5_l1k3_y0u_solv3d_it_b57ed0cd}

## Conclusão

Este desafio de Web Exploitation é interessante, porque explora a vulnerabilidade de SQL Injection, que é um tipo de ataque bastante conhecido.
Para prevenir esse tipo de ataque, é importante implementar as seguintes medidas de segurança no site:

- Uso de consultas parametrizadas: Preparar as declarações SQL e armazená-las em uma variável antes da execução para evitar que um atacante insira declarações no banco de dados. 

- Validação de entrada de dados: Verificar se as entradas do usuário são válidas e não contêm dados maliciosos (filtrar as entradas). 

- Uso de procedimentos armazenados: Utilizar procedimentos armazenados para controlar o acesso ao banco de dados e evitar que consultas maliciosas sejam executadas. 

- Higienização das entradas do banco de dados: Limpar as entradas do banco de dados antes de executar consultas para remover dados maliciosos. 

- Acesso com privilégios mínimos: Limitar o acesso ao banco de dados a usuários e grupos que realmente precisam de acesso. 
