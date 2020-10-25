<p align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="https://i.ibb.co/2K9m2tV/final2.png" alt="Logo" width="528" height="206">
  </a>

  <h3 align="center">Ansible-Wiki.js</h3>

  <p align="center">
    Instale e Configure o Wiki.js com Ansible e Vagrant
    <br />
  </p>
</p>

## Sobre o Wiki.js
[Wiki.js](https://wiki.js.org/) é um mecanismo wiki (Knowledge base) executado em Node.js e escrito em JavaScript. É uma ótima alternativa open-source para gestão do conhecimento. A aplicação é altamente extensível por meio de uma variedade de módulos, permitindo diferentes maneiras de lidar com autenticação, armazenamento e conectar vários bancos de dados, bem como um mecanismo de pesquisa opcional de sua escolha.

## Requisitos
Para iniciarmos este projeto, é necessário realizar a instalação do [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) e do [Vagrant](https://www.vagrantup.com/downloads).

## Iniciando máquinas virtuais com Vagrant
Primeiro, vamos começar com o clone deste repositório em sua máquina local.
```sh
$ git clone https://github.com/sidney-neto/ansible-wikijs
```
Em seguida, ao acessar o diretório deste projeto, inicialize a configuração das máquinas virtuais com o Vagrant. Como o projeto foi desenvolvido em Windows, realizei a configuração de uma segunda máquina virtual para execução do Ansible com playbook.
```sh
$ vagrant up
```
Após finalizar a inicialização das máquinas virtuais, acesse via SSH o Ansible host.
```
$ vagrant ssh ansible
```

## Iniciando configuração do Wiki.js com Ansible
Acesse a pasta compartilhada `/vagrant` e teste a conexão com o Wiki.js host.
```
$ ansible all -i hosts -m ping
```
```JSON
# Saída do ping
192.168.1.40 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```
Por fim, realize a execução do playbook para iniciar as tasks de configuração do Wiki.js.
```
$ ansible-playbook provisioning.yml -i hosts
```
```
# Saída do playbook
PLAY [all] *********************************************************************************************************

TASK [Gathering Facts] *********************************************************************************************
ok: [192.168.1.40]

TASK [instalando dependências] *************************************************************************************
```
## Acesso Web
Ao finalizar todas as tasks, acesse através do navegador o endereço `http://192.168.1.40:3000` e finalize o setup inicial.
<p align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="https://i.ibb.co/0tvgfdF/wiki.png" alt="Logo" width="707" height="661">
  </a>
</p>
  
## Vagrant Box
Disponível também, o Vagrant box do setup do Wiki.js realizado com Ansible. Realize o download através do Vagrant Cloud: [sidneyramosneto/wikijs](https://app.vagrantup.com/sidneyramosneto/boxes/wikijs)
