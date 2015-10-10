# Projeto Base
Neste projeto contém a estrutura base para ser tomada como exemplo no desenvolvimento de projetos web.

### Estrutura
A estrutura aqui definida contempla 3 divisões, estas são:

  - RESTful API
  - Admin Panel
  - FrontEnd 
    
Sendo estes estruturados da seguinte forma:
 - www [dados das aplicações]
    - api
    - frontend
    - admin
- sites [virtualhosts]
    - api.conf
    - frontend.conf
    - admin.conf
- logs [logs do apache]
    -  error.log
    -  access.log

### Execução
Neste projeto, também foi configurado o Vagrant buscando facilitar sua replicação em diversos ambientes de desenvolvimento.

No Vagrantfile estão parametrizadas as instalações dos seguintes pacotes:

- Apache2
- PHP5
- Phpunit
- MySql
- Curl

E para auxiliar no desenvolvimento:
- Htop
- Git
- Nmap
- Npm
- Composer
    
Ao inicializar o Vagrant serão compartilhados os seguintes diretórios:

- www:/vagrant_data
- sites:/etc/apache2/sites-available
- logs:/var/log/apache2

### Uso

Após configurar os [virtualhots] que serão utilizados, basta executar:

```sh
$ vagrant up
```
Após isto será necessário tornar disponíveis os [virtualhots] configurados no diretório *sites*. Para isto você irá realizar o acesso ssh na máquina virtual utilizando o vagrant:
```sh
$ vagrant ssh
```
E executará o comando para ativar sites no apache2:
```sh
$ sudo a2enmode admin api frontend
```
E para finalizar será necessário recarregar o servico apache2:
```sh
$ sudo service apache2 reload
```

### Versão
1.0.0

License
----
Copyright © Luizcoder \
Licensed under the MIT license.

