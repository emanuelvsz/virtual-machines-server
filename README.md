# Roteiro para realização do projeto do 2º bimestre das disciplinas de Infraestrutura e Serviços de Redes e Projetos de Redes

Objetivo: criação de *8* máquinas virtuais e criação de uma conexão entre quatro computadores com duas VMs cada.

>**_NOTA:_**
Inicialmente, serão criadas duas máquinas virtuais em cada PC do grupo
>**_**




<h2> Criando uma Máquina Virtual </h2>

  1. Criando uma VM utilizando um arquivo .OVA 

  Figura 01: Importando o arquivo .OVA
  
  <img width="482" alt="import-ova1" src="https://user-images.githubusercontent.com/84058517/183082785-16a33090-0acb-49f7-966b-da90f937ab38.png">
  
  <br>
  
  Figura 02: Especificações da Maquina Virtual .OVA

  
  ![criandoVM2](https://user-images.githubusercontent.com/84058517/183087854-27897109-880d-49dd-a3de-c2efda3be598.png)


  Após a criação das duas VMs, é obrigatório os seguintes passos em <b>CADA</b> Máquina Virtual
  
  2. Configurando VM
  
  2.1. Para instalar o pacote de rede
  ```
  sudo apt install net-tools -y
  ```
  
  2.2 Para visualizar as interfaces de rede
  ```
  ifconfig -a
  ```
  
  2.3 Definindo tipo de rede(no Virtual Box)
  
  * Para fazer com que as maquinas virtuais do PC se comuniquem entre sí, é necessário coloca-las no modo de <b>Rede Interna</b>
    ~adicionar imagem~

  3. Logando nas VMs

  após tudo ter sido realizado, é necessário logar como administrador para prosseguir
  
  ### Para logar 
  
  ```
  ubunto login: administrador
  senha: adminifal
  ```
  ~adicionar imagem~
  
  <h2>Configuração estática de endereço IP na interface de rede</h2>
    * Primeiramente é necessário modificar o arquivo que configura as interfaces de rede
    * Esse arquivo é do tipo .YAML e fica no diretório ``/etc/netplan``
  
