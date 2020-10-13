# Conexão dial-up 
    Conexão dial-up é o nome das conexões feitas via interface de fax-modem  modulador/demodulador.
    O fax-modem é uma placa normalmente PCI.
 
 ![alt text](./Imagem/fax_modem.jpg "Fax modem" )

O fax-modem possui normalmente dois conectores do tipo RJ-11

    O conector LINE  vai para a tomada do telefone na parede.
    O conector PHONE vai para o seu telefone. 
 ![alt text](./Imagem/fax_modem_ports.jpg "Portas Fax modem" )    
 

# O que posso fazer com um modem?

    Ligação telefonica pelo computador.
    Receber ligaçoes pelo computador.
    Conectar a internet atravez de provedor de internet.
    Conectar dois computadores em rede atravez de dois modens. 
    Reconhecer o numero do chamador  assim como faz um aparelho de BINA (B Identify Number of A- B Identifica Número de A). 
    para essa última funcionalidade talvez seja preciso contratar o serviço com sua operadora telefônica.
 
 # Comandos AT
    O modem é comandado por um conjunto de comandos padrão embutidos pelo fabricante chamados de comandos AT.
    Todos os modem possuem esse conjunto de comandos, alguns podem ter alguns comandos diferenciados com finalidades 
    específicas para cada equipamento, além dos que são exigidos pelo padrão de fabricação.  
    É importante procurar e verificar o conjunto de comandos AT do seu modem,
     para ver exatamente o que é possível ser feito com ele. 

# Conectar-se ao MODEM
Para conectar-se ao MODEM será preciso saber em que porta serial ele foi instalado.
 
  ![alt text](./Imagem/windows_driver_modem.jpg "Portas Fax modem" )    
  
 

 # Configurando o PuTTY

Para esse tutorial eu usei o PuTTY para acesso a porta serial, que é gratuito e pode ser encontrado em http://www.putty.org/
 

Abra o PuTTY, em Connection Type selecione Serial, no campo Serial Line digite o nome da porta COM onde o seu modem está instalado, no meu caso foi a COM7 e deixe o campo Speedno valor padrão, 9600. Clique no botão Open:

 

![alt text](./Imagem/PuTTY_open.jpg "PuTTY open" )   

Será aberta outra janela, preta, sem nada escrito. Caso isso ocorra quer dizer que até agora foi tudo certo!


![alt text](./Imagem/PuTTY_idle.jpg "PuTTY idle" )  
 

Você terá que digitar um comando para que tudo o que fizermos a seguir seja mostrado nessa janela. 
Esse comando não aparecerá enquanto você estiver digitando,
 ao terminar de digitá-lo você deve teclar ENTER e nessa janela será apresentada a resposta OK.
  Se a resposta for ERROR, tente digitá-lo novamente.
  
    O comando para ver o que se esta digitando, ou seja, ativar o echo de comandos, é o que segue:
      {code}
      ATE1
      {/code}
     
    para desativar o echo de comandos o comando é: 
      {code}
      ATE0
      {/code}
    
    Assim, seguindo essa lógica, mais ou menos padrão para todos os comandos, 
    quando o comando recebe o valor 0 (zero) ele é desativado e quando recebe 1 (um) ele é ativado. 
    Pensando assim fica fácil de entender os comandos AT.
 
 ![alt text](./Imagem/ok.jpg "PuTTY ok" )  

# Caller ID
     Ativar o reconhecimento de chamadas (caller ID) use o seguinte comando:
        {code}
        AT#CID=1
        {/code}
     E para desativar o reconhecimento de chamadas:
         {code}
         AT#CID=0
         {/code}   

  ![alt text](./Imagem/PuTTY_ok.jpg "PuTTY ok" )  

 

Feito isso, de outro telefone, ligue para o número da linha telefônica que está conectada no modem, você deverá ver algo parecido com isso:

   ![alt text](./Imagem/receiver.jpg "PuTTY ok" )  

 

    Quando o telefone toca o modem emite mensagem de RING, 
    logo que possível (caso você tenha essa facilidade em sua linha telefônica)
    o número do chamador (campo NMBR) é mostrado, precedido da data (campo DATE) e horário (campo TIME) daquela ligação.



# lista de comandos AT para modem:

| comandos   |      descrição                                                                                                                                                                                       |  
|:-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   AT&Zx=y  |  Armazenar o número telefônico y na posição de memória x                                                                                                                                             | 
|   AT&Zx?   |  Mostrar o número telefônico existente na posição x                                                                                                                                                  |  
|   ATDSx    |  Discar para o número telefônico x (digitar o número telefônico, no caso de PABX usar o comando abaixo)                                                                                              |       
|   ATD0,x   |  Discar para o número telefônico x usando o prefixo 0 para obter linha em PABX                                                                                                                       |
|   ATDT     |  Ativa discagem por tons                                                                                                                                                                             | 
|   ATDP     |  Ativa discagem por pulsos                                                                                                                                                                           |
|   ATDL     |  Discar para o último número discado (redial)                                                                                                                                                        |
|   ATDL?    |  Exibir o último número discado                                                                                                                                                                      |
|   ATI1     |  Exibir informações sobre o modem                                                                                                                                                                    |
|   ATI2     |  Exibir informações sobre a memória RAM do modem                                                                                                                                                     |
|   ATI3     |  Exibir informações sobre o firmware do modem                                                                                                                                                        |
|   ATI4     |  Exibir as configurações atuais do modem                                                                                                                                                             |
|   ATL1     |  Ativa o som do modem com volume baixo (ouvir a ligação pelo modem)*1                                                                                                                                |
|   ATL2     |  Ativa o som do modem com volume médio (ouvir a ligação pelo modem)* 1                                                                                                                               |
|   ATL3     |  Ativa o som do modem com volume alto (ouvir a ligação pelo modem)* 1                                                                                                                                |
|   ATL0     |  Desativa o som do modem                                                                                                                                                                             |
|   ATM0     |  O som do modem ficará sempre desligado                                                                                                                                                              |
|   ATM1     |  O som do modem ficará ligado até que uma conexão seja estabelecida                                                                                                                                  |
|   ATM2     |  O som do modem ficará sempre ligado                                                                                                                                                                 |
|   ATH0     |  Desligar uma ligação (colocar no gancho)                                                                                                                                                            |
|   ATH1     |  Atender a uma ligação (tirar do gancho)                                                                                                                                                             |
|   ATZ      |  Desligar uma ligação                                                                                                                                                                                |
|   ATE0     |  Desativa o echo de comandos (o que é digitado não aparece na tela)                                                                                                                                  |
|   ATE1     |  Ativa o echo de comandos (o que é digitado aparece na tela) *1 ao ouvir a ligação pelo modem caso o som do computador estiver ativado a ligação será ouvida pelas caixas de som ou fones de ouvido; |

 # se existir erro verifique ANTES
     se a Placa do modem esta conectada na placa mãe.
     se o driver esta instalado corretamente no Windows.
     se os fios do da linha telefônica e do telefone devidamente conectados.
