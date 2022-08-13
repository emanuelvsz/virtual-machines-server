# Roteiro para realização do projeto do 2º bimestre das disciplinas de Infraestrutura e Serviços de Redes e Projetos de Redes

Objetivo: criação de *8* máquinas virtuais e criação de uma conexão entre quatro computadores com duas VMs cada.

>**_NOTA:_**
Inicialmente, serão criadas duas máquinas virtuais em cada PC do grupo
>

# Sumário 

 * <a href="#vm-creating">Criando máquina virtual</a>
 * <a href="#vm-definitions">Definições</a>
 * <a href="#vm-installingssh">Instalando o SSH</a>
 * <a href="#vm-finalpasses">Passos finais</a>
 * <a href="#vm-errors">Erros</a>



<h2> Criando uma Máquina Virtual </h2>

  1. <section id="vm-creating"> criando uma VM utilizando um arquivo .OVA </section>

  Figura 01: Importando o arquivo .OVA
  
  <img width="482" alt="import-ova1" src="./img/figure-01.png">
  
  <br>
  
  Figura 02: Especificações da Maquina Virtual .OVA

  
  <img width="482" alt="import-ova1" src="./img/figure-02.png">


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

  Após tudo ter sido realizado, é necessário logar como administrador para prosseguir
  
   ### Para logar 
  
   ```
   ubunto login: administrador
   senha: adminifal
   ```
   
   Figura 03: 
   
  <img width="482" alt="import-ova1" src="./img/figure-03.png">
  
  <section id="vm-definitions"><h1>Definições</h1></section>
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
  
  ## Inserindo um nome para a rede ``hostname``

  ```
  sudo hostnamectl set-hostname nome-do-hostname
  ```
  
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
  
  Figura 04:
  
  <img width="482" alt="import-ova1" src="./img/figure-04.png">


  * enps0s3: # nome da interface que está sendo configurada. Verifique com o comando 'ifconfig -a'
  * adresses: # IP e Máscara do Host.
  * gateaway: # IP do Gateway
  * dhcp4: false # dhcp4 false -> cliente DHCP está desabilitado, logo o utilizará o IP do campo 'addresses'    

#### Após ter modificado o arquivo .YAML, as modificações terão que ser salvas com o seguinte comando: 

```
sudo netplan apply
```

  ## <section id="vm-installingssh">Começando a instalar o ``SSH Server``</section>
  
   1. Pré-requisitos: <br>
       1.1. Alterar na configuração da máquina a configuração de rede para ``NAT``. <br>
       1.2. Comentar as linhas do endereço IP estático.(No arquivo .YAML) <br>
       1.3. Ativar o DHCP. (No arquivo .YAML) <br>

        Figura 05: 
        
        <img width="482" alt="import-ova1" src="./img/figure-05.png">

   2. Instalando o SSH Server <br>
   * ### Certifique-se que a Máquina Virtual está conectada a internet <br>
       * Para atualizar as definições e versões de pacotes/bibliotecas dos repositórios do Ubuntu <br>
       ```
       sudo apt update
       ```
       * Para atualizar os pacotes com as novas definições setadas com o update <br>
       ```
       sudo apt upgrade -y
       ```
   * ### Instalando o SSH <br>
      ```
      sudo apt-get install openssh-server
      ```
    
       #### Após ter feito o processo inteiro, sem nenhum empecilho, prossiga:
       
       * Verifique se o ssh foi instalado corretamente: 

         ```
         systemctl status ssh
         ```

       * Verifique o status das portas do sistema:

         ```
         netstat -an | grep LISTEN. # verifique se a porta 22 está LISTENING
         ```
         
         Figura 06:
         
         <img width="482" alt="import-ova1" src="./img/figure-06.png">

         
       * Para garantir o funcionamento do SSH Server, é necessário habilita-lo no firewall. Faça-o: 
         ```
         sudo ufw allow ssh
         ```
       * Ative o firewall: 
         ```
         sudo ufw enable
         ```
       #### Após ter concluído o processo, volte para as configurações anteriores:
       * Coloque a configuração de rede da VM como ``Modo Bridge``
       
       Figura 07: 
       
       <img width="482" alt="import-ova1" src="./img/figure-07.png">
       
       * Tire os comentários do arquivo .YAML
       
       Figura 08:
       [
       <img width="482" alt="import-ova1" src="./img/figure-08.png">


      >**_OBS:_**
       Lembre-se de dar o comando ``sudo netplan apply`` para salvar as alterações feitas
      >

       ## Agora a parte física:
      
       * Conecte todos os computadores utilizando ``cabos de rede`` e um ``switch``
       <br>

      Figura 09            |  Figura 10
      :-------------------------:|:-------------------------:
      <img width="300" alt="import-ova1" src="./img/figure-09.jpeg"> |  <img width="300" alt="import-ova1" src="./img/figure-10.jpeg">
      Conectando o  ``cabo de rede`` à entrada da <br> ``placa de rede`` do computador | Conectando a outra ponta do cabo de rede ao ``switch``

       # <section id="vm-finalpasses">Ultimos passos: </section>
       * Logar em outra máquina virtual(pode ser até em outro PC caso os dois ou mais estejam conectados via cabeamento):
       
       Exemplo: ``ssh usuario@ipderedeunico``
       
       Exemplo: 
       ```
       ssh administrador@192.168.14.53
       ```
       
       Após isso, está pronto o funcionamento do servidor. 
       
     ### <section id="vm-errors"><h1>Prováveis erros</h1></section>
       
     ### Ssh não instalado: 
     
     Figura 11: 
       
     <img width="300" alt="import-ova1" src="./img/figure-11.png">

     ### Firewall não está ativo:
       
     Figura 12: 
     
     <img width="300" alt="import-ova1" src="./img/figure-12.png">
     
     * Para ativa-lo, basta dar o comando ``sudo ufw enable``
       
     ### Firewall não está permitindo o ``ssh``(verificar a porta 22)

