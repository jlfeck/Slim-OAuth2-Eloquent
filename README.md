# Slim-OAuth2-Eloquent

Este repositório contém código para desenvolvedores que precisam iniciar uma aplicação utilizando os conceitos RESTFul com [Slim Framework](http://www.slimframework.com/), porém, não querem passar pala fase de estruturação e configuração de ferramentas como [Eloquent ORM](http://laravel.com/docs/4.2/eloquent#), [OAuth](http://oauth.net/) e [Slim-Monolog](https://github.com/Flynsarmy/Slim-Monolog). *Slim-OAuth2-Eloquent* já contém todas estas ferramentas configuradas e prontas para uso.

## Requerimentos
PHP >= 5.4.0

## Instalação
* Download [`composer.phar`](https://github.com/composer/composer) 
```sh
$ curl -sS https://getcomposer.org/installer | php
```
* Instalar dependências
```sh
$ composer install
```
* Criar banco de testes [SQLite](http://www.sqlite.org/)
```sh
$ php share/init/init.php
```

## Usar

### Banco de dados

O banco de dados que foi criando, dentro do subdiretório *share/init*, contém um usuário de teste. Este será usando para ilustrar o uso da API.
```
username: usertest
password: test
```

### Pasta *Core* e arquivo *routes.php*

A pasta `Core` e o arquivo `routes.php` é onde deve estar todo o fluxo do projeto. Nestes locais ficarão os código que não devem ser atualizados por novas versões do projeto `Slim-OAuth2-Eloquent`.
Para não haver problemas é muito importante que o desenvolvedor inclua estes no `.gitignore` de seu projeto.

### Solicitar um token para acesso e atualizar token (Refresh token)

Para obter um token de acesso ou atualizar o token existente, a solicitão deve ser feita utilizando o método `POST` e `Content-Type: application/x-www-form-urlencoded`. Os dados nescessários são:
  
##### Solicitação
```
grant_type: password
client_id: testclient
client_secret: secret
username: usertest
password: test
```
  
##### Atualização
```
grant_type: password
client_id: testclient
client_secret: secret
username: usertest
password: test
```

### Acessar dados com token de acesso obtido na solitação (Access token)

O acesso aos dados da API acontece dentro dos padrões *RESTful* (`GET`, `POST`, `PUT`, `DELETE`). Ao utilizar qualquer um destes métodos é obrigatório o envio do 'token' obtido na solictação. O mesmo precisa ser enviado no 'header' da requisição 'http' através do parametro 'Authorization' e este deve ser da seguinte foma:

```
Authorization: Bearer d7TSwi1dXK3F1sN78tTEPDGOmD9c2oWmRFu6hrj6
```

*OBS.: O hash utilizado como token é meramente ilustrativo, devendo ser substituído pelo obtido na solicitação/atualização de token*

## Links
* [Slim Framework](http://www.slimframework.com/)
* [Eloquent ORM](http://laravel.com/docs/4.2/eloquent#)
* [OAuth](http://oauth.net/)
* [Slim-Monolog](https://github.com/Flynsarmy/Slim-Monolog)
* [Composer](https://github.com/composer/composer)
* [SQLite](http://www.sqlite.org/)
* [PHP](http://php.net/)
* [oauth2-server](https://github.com/thephpleague/oauth2-server)

## Referências utilizadas
* [Best Practices for Designing a Pragmatic RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
* [An Introduction to OAuth 2](http://www.slideshare.net/aaronpk/an-introduction-to-oauth-2)
* [RFC3986](http://www.ietf.org/rfc/rfc3986.txt)

## Suporte
Bugs, features, sugestões ou dúvidas utilizar [GitHub](https://github.com/leoniralves/Slim-OAuth2-Eloquent/issues)

## Autor
Leonir Alves - https://twitter.com/leonir_ad