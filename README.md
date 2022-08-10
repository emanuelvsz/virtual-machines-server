# Roteiro para realização do projeto do 2º bimestre das disciplinas de Infraestrutura e Serviços de Redes e Projetos de Redes

Objetivo: criação de *8* máquinas virtuais e criação de uma conexão entre quatro computadores com duas VMs cada.

>**_NOTA:_**
Inicialmente, serão criadas duas máquinas virtuais em cada PC do grupo
>




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
  
  <h1>Definições</h1>
  Após ter concluído os passos anteriores, é necessário declarar um IP único na rede para todas as VMs de cada computador.
  
  * Para isso, foi feita uma tabela com todos os dados referentes a cada computador:
  
 
 <h2>Tabela 01</h2>
 
 <table>
  <tr>
    <th>Nome dos integrantes</th>
    <th>Nome dos PCs</th>
    <th>IP de rede</th>
    <th>IP de broadcast</th>
    <th>Intervalo de IPs</th>
  </tr>
  <tr>
    <td>Leonardo Ferreira</td>
    <td>PC1-GRUPO4</td>
    <td>192.168.14.48/28</td>
    <td>192.168.14.63</td>
    <td>192.168.14.[48-63]/28</td>
  </tr>
  <tr>
    <td>Julia Eloizi</td>
    <td>PC2-GRUPO4</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Emanuel Vilela</td>
    <td>PC3-GRUPO4</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Micaele Rayanne</td>
    <td>PC4-GRUPO4</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

>**_NOTA:_**
Todos os quatro PCs terão um IP estático identico
>

 <h2>Tabela 02</h2>


  <table>
    <tr>
      <th>Nome das VMs</th>
      <th>IP da VM</th>
      <th>hostname</th>
      <th>FQDN da VM</th>
      <th>Aliase da VM</th>
    </tr>
    <tr>
      <td>PC1-GRUPO4-VM01</td>
      <td>192.168.14.49</td>
      <td>PC1-GRUPO4-VM01</td>
      <td>leonardo-vm01.grupo4-914.ifalara.net</td>
      <td>burro1</td>
    </tr>
    <tr>
      <td>PC1-GRUPO4-VM02</td>
      <td>192.168.14.50</td>
      <td>PC1-GRUPO4-VM02</td>
      <td>leonardo-vm02.grupo4-914.ifalara.net</td>
      <td>burro2</td>
    </tr>
    <tr>
      <td>PC2-GRUPO4-VM03</td>
      <td>192.168.14.51</td>
      <td>PC2-GRUPO4-VM01</td>
      <td>julia-vm03.grupo4-914.ifalara.net</td>
      <td>ratocego1</td>
    </tr>
    <tr>
      <td>PC2-GRUPO4-VM04</td>
      <td>192.168.14.52</td>
      <td>PC2-GRUPO4-VM02</td>
      <td>julia-vm04.grupo4-914.ifalara.net</td>
      <td>ratocego2</td>
    </tr>
    <tr>
      <td>PC3-GRUPO4-VM05</td>
      <td>192.168.14.53</td>
      <td>PC3-GRUPO4-VM01</td>
      <td>emanuel-vm05.grupo4-914.ifalara.net</td>
      <td>farquaad1</td>
    </tr>
    <tr>
      <td>PC3-GRUPO4-VM06</td>
      <td>192.168.14.54</td>
      <td>PC3-GRUPO4-VM02</td>
      <td>emanuel-vm06.grupo4-914.ifalara.net</td>
      <td>farquaad2</td>
    </tr>
    <tr>
      <td>PC4-GRUPO4-VM07</td>
      <td>192.168.14.55</td>
      <td>PC4-GRUPO4-VM01</td>
      <td>micaele-vm07.grupo4-914.ifalara.net</td>
      <td>dorisfeia1</td>
    </tr>
    <tr>
      <td>PC4-GRUPO4-VM08</td>
      <td>192.168.14.56</td>
      <td>PC4-GRUPO4-VM02</td>
      <td>micaele-vm08.grupo4-914.ifalara.net</td>
      <td>dorisfeia2</td>
    </tr>
  </table>
  
  <h2>Configuração estática de endereço IP na interface de rede</h2>
  
  * Primeiramente é necessário modificar o arquivo que configura as interfaces de rede
  * Esse arquivo é do tipo .YAML e fica no diretório ``/etc/netplan``
  * Inicialmente, verifique o nome do arquivo em seu computador da seguinte forma:

  ```
  ls -la /etc/netplan
  ```
  
  ## Editando o .YAML
  
  ```
  sudo nano /etc/netplan/01-netcfg.yaml 
  ```
  
  Após ter aberto o arquivo para edição, modifique as configurações antigas para as referente ao <b>PC</b> e a <b>VM</b>. Por exemplo, na figura à seguir, foi utilizado o PC3-VM2
  
  >**_OBS:_**
  Essas modificações deverão ser feitas em <b>TODAS</b> as VMs
  >
  
  Figura 03:
  
 ![nome](https://user-images.githubusercontent.com/84058517/183898632-661ef4a0-f276-4fc2-926d-793237830fec.png)


  * enps0s3: # nome da interface que está sendo configurada. Verifique com o comando 'ifconfig -a'
  * adresses: # IP e Máscara do Host.
  * gateaway: # IP do Gateway
  * dhcp4: false # dhcp4 false -> cliente DHCP está desabilitado, logo o utilizará o IP do campo 'addresses'    

## Após ter modificado o arquivo .YAML, as modificações terão que ser salvas com o seguinte comando: 

```
sudo netplan apply
```

##
