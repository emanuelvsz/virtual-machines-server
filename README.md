# Roteiro para Projeto 2º Bimestre das Disciplinas de Infraestrutura e Serviços de Redes e Projetos de Redes

Roteiro de aula para a criação de máquinas virtuais e criação de uma conexão entre quatro computadores com duas VMs cada.

>**_NOTA:_**
Inicialmente, será criada as duas máquinas virtuais em cada PC do grupo
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
