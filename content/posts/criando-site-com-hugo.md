---
author: "Milton Jacomini"
date: "2019-02-17T17:14:00-03:00"
lastmod: "2019-02-17T17:14:00-03:00"
title: Criando site com hugo (GoLang)
tags: [
    "go",
    "golang",
    "templates",
    "themes",
    "development",
]
---

## Introdução

Fala galera, suave!?

Bom, to a um tempo para começar a escrever umas coisinhas que vou fazendo e aprendendo 
e agora resolvi iniciar essa parada de vez! =)

O [`Hugo`](https://gohugo.io/) é um framework escrito em 'Go' mais uma das linguagens do Pai Google! Eu to começando
a brincar com Go e achei interessante montar o site com um framework da linguagem.

Na página deles você acha as instruções para [download](https://golang.org/dl/) e [instalação](https://golang.org/doc/install).

Feito isso, bora pro `Hugo`

## Hugo

##### *Instalação*

Muito simples, se você já for usuário dos shells da vida já vai matar rapidão. 
Senão for, basicamente existem gerenciadores de pacotes para instalação de softwares via [shell](https://swcarpentry.github.io/shell-novice/reference/). 

Se você for usuário de MacOS vai usar o `brew` se você for usuário de Windows 
vai usar o `choco` ou `scoop`. Mais sobre na [página](https://gohugo.io/getting-started/installing) deles.

##### *Primeiros passos*

Para se certificar que o `Hugo` está instalado digita ae:
```
hugo version
```

Depois disso acessa lá seu diretório que quer criar o site e manda:
```
hugo new site {nomedoseusite}
```

Se você digitar um ``ls`` vai ver que já existe a pasta que contém todo o conteúdo
do seu site =), bora acessar ela ``cd {nomedapasta}``

já vamos direto para o que interessa, que é o arquivo de `config`.

Meu editor preferido hoje é o VSCode então usarei:
```
code config.toml
```

Mas você pode alterar code para seu editor de texto preferido trocando a primeira instrução do código acima ou simplesmente abrir o arquivo direto pelo seu editor.

vamos por partes..rs


Esse deve ser seu arquivo quando aberto:
```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
``` 

Isso é o que deve ter aparecido pra você.

Imagino que sem muito segredo, certo!? URL base da sua aplicação, a linguagem utilizada
nos códigos e o título do seu site.

O meu ficou assim:
```
baseURL = "http://miltonjneto.com.br" <- Meu domínio
languageCode = "en-us" <- Não alterei a linguagem mantive o englishh
title = "Milton Jacomini"
```

Por enquanto sem segredo né!? Bem easy, na real você vai ver que tudo é bem easy..rsrs

Agora a parte mais divertida e demorada dependendo da pessoa, rsrsrsrs! Escolher o Tema,
depois de escolhido vamos adiciona-lo ao site fazendo o seguinte.

```
# Entra na pasta dele
cd {seusite}

# Para iniciar um repositório git na raiz do seu projeto
git init
git submodule add https://github.com/budparr/{pathdotema}.git {pathdotema}

# ex: tema escolhido foi o themes/ananke
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

```
Se você não é um usuário do Git ou não quer fazer isso agora, acessa o repositório do seu tema e faz o download da branch master.

{{< figure src="images/download-zip-github.gif" title="Download tema github" >}}

Feito isso faz a extração do arquivo zip e renomeia ele para o nome simples do tema,
como por exemplo se era `gohugo-theme-ananke` renomeia só para `anake`. Copia esse arquivo para
a pasta `{seusite}/themes/{suapastarenomeada}`.

voltamos ao arquivo de configuração que usamos lá no começo `config.toml`.

```
baseURL = "http://miltonjneto.com.br"
languageCode = "en-us"
theme = "ananke" #Adicione essa linha com o nome que da pasta que vc jogou na `themes`
title = "Milton Jacomini"
```

Feito isso, cria um post novo só pra ver a magia da coisa.

```
hugo new posts/meu-primeiro-post.md 
```

E agora vamos iniciar o servidor do `Hugo` e ver o site online (Localmente, por enquanto..rs)

Na raiz do projeto:
```
hugo server -D
```

Já deve ter visto ele rodando né!? =)

E ai curtiu?

Estou aberto a feeback`s, abss.