---
author: "Milton Jacomini"
date: "2019-03-08T00:30:00-03:00"
title: Hugo on Github Pages (gh-pages)
tags: 
  - github
  - hugo_on_github
  - github-pages
  - gh-pages
---

Salve salve meu povo, novo post...

Como tinha comentado, esse é sobre colocar seu blog feito em Hugo no Github Pages

## Introdução

Vou considerar que você é um usuário do Github e pular a explicação sobre os comandos relacionados ao Git. 

Ok? .. Mas claro, se tiver dúvidas sobre o que eu não falar pode mandar nos comentários que eu respondo. =)

Sobre o [`Github Pages`](https://pages.github.com/), é uma ferramenta que o Github disponibiliza para que você
possa publicar paginas estáticas. Muito usado para montar um site simples de apresentação, na maioria das vezes
sobre `Frameworks`,`Libs`,`Tutoriais` e etc.. Coisas desse tipo 
(E que muitas vezes já fica junto com o código do projeto).

Com essa funcionalidade muita gente começou a montar blogs e páginas de apresentação e publicar nesse hospedeiro
free de sites estáticos. 

sem mais delongas,

Mãos a obra...

## Setup do seu projeto

Para começar vamos considerar que você criou seu repositório no github.

O meu é `https://github.com/Miltonjacomini/demo-blog `, você pode criar ele pela plataforma do github direto ou por linha de comando, criado o seu repositório você precisa indicar no seu projeto que está usando esse diretório.

<details>
  <summary>Processo detalhado para criar repositório e linkar no repositório remoto.</summary>

  Para iniciar um repositório na raiz do seu projeto:
  ```
    git init
  ```

  Adicione tudo que tem no repositório e faça o primeiro commit para que a branch `master` seja criada
  no repositório seu local.
  ```
    git add .
  ```
  {{< figure src="../images/git-add-status-scroll.gif" alt="Scroll do resultado do git add" >}}
  Algo parecido vai acontecer ai..

  ```
    git commit -m "Adiciona arquivos no projeto"  
  ```
  E o depois do commit mesma coisa: 
  {{< figure src="../images/git-commit-scroll.gif" alt="Scroll do resultado do git commit" >}}

  Para linkar esse repositório que até o momento é `local` para um repositório `remoto`,
  `git remote add origin linkdoseurepositorio` no meu caso ficou assim:
  ```
    git remote add origin git@github.com:Miltonjacomini/demo-blog.git 
  ```

  E fazer o push para enviar para o repositório remoto que vc acabou de linkar.
  ```
    git push -u origin master
  ```
</details>
<br/>

## Configurando o GitHub Pages

Considerando então que você já tem seu projeto no github vamos acessar o `Settings` do repositório e habilitar o github pages.

{{< figure src="../images/github-pages-none.png" alt="Git hub pages" >}}

Podemos ver que ele tem uma opção onde você pode selecionar qual será o `Source` do seu site. 

Isso nada mais é do que o diretório que o GitHub Pages vai considerar como `raiz` do seu projeto. Que é onde vai estar seu código estático. 

No meu caso eu optei por deixar o projeto todo do blog no github o que me facilitaria a manutenção dele fora de casa, mas você pode optar por deixar na raiz do seu projeto só o conteúdo já gerado pelo Hugo.

Que por default fica em `public`.

Se você não quiser expor seu projeto, inicia seu git na pasta public e escolhe o `Source` como master.

> Se quiser ver o Hugo gerando o conteúdo faz o teste. 
Entra na pasta public na raiz do seu projeto e apaga tudo, depois gera denovo com 
`hugo -t nomedoseutema` na raiz do projeto.

Por deixar meu projeto todo no github eu não posso deixar que a minha `master` a raiz do meu projeto seja o `Source` pois lá vai ter um monte de código que o Hugo entende e utiliza.

Preciso então que o GitHub Pages saiba que meu `Source` é outro, no caso `/docs` diretório default no GitHub Pages.

{{< figure src="../images/github-pages.png" alt="Git hub pages" >}}

## Alterando configurações do seu site

Seguindo do jeito que eu fiz, adicionei no meu `config.toml` aquele arquivo que alterei no [primeiro post](https://miltonjneto.com.br/posts/criando-site-com-hugo/), o arquivo de configurações do seu site em `Hugo` que fica na raiz do projeto.

Lá eu adicionei duas coisas,
uma para alterar o local aonde o Hugo vai jogar meu conteúdo estático compiladinho bonitinho:
```
publishDir = "docs"
```

e a outra foi para que o meu site estático seja gerado com o path (diretório) dos arquivos `html, css e js` apontando para o lugar certo:
```
baseUrl = https://miltonjacomini.github.io/demo-blog/ 
```

Essa é a url que é exibida nas configurações do Github Pages.
{{< figure src="../images/github-pages-link.png" alt="Git hub pages" >}}

Bom, feito isso.
Seu arquivo deve estar assim:
```
baseURL = "https://miltonjacomini.github.io/demo-blog/"
languageCode = "en-us"

Title = "Theme Demo"
theme="ananke"

publishDir = "docs"
```

Cheeeeck, lindesas.

## Final e review

Agora é só gerar novamente os arquivos do Hugo, com o comandinho maroto:
```
  hugo -t "nomedoseutema"
```

Adicionar tudo no git e subir.

Aquele combo exxperto `git add `,`git commit -m 'msg de commit'` e `git push`.

Logo seu site vai estar aparecendo bonitão no link que o GitHub Pages te disponibilizou
e você adicionou no arquivo de configurações.

no meu caso: https://miltonjacomini.github.io/demo-blog/

{{< figure src="../images/finish-post-2.gif" alt="Review do post em um gif" >}}

E assim finalizamos..

Como de praxe vou sempre deixar o próximo assunto que vou falar, e vai ser:
Um serviço REST (SpringBoot + React) para upload de arquivos no S3 da Amazon.

Feedbacks são bem vindos =)

Absss.