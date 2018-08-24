---
title: "Config. Polít. de Qual. de Serv. (QoS) p/ Clientes Exec. no W. Server 7 ou W. 8"
TOCTitle: "Config. Polít. de Qual. de Serv. (QoS) p/ Clientes Exec. no W. Server 7 ou W. 8"
ms:assetid: efff2b98-b3fb-4183-a4f0-329a9105ce2c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205371(v=OCS.15)
ms:contentKeyID: 49308557
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando as Políticas de Qualidade de Serviço (QoS) para Clientes Executando no Windows Server 7 ou Windows 8

 

_**Tópico modificado em:** 2016-03-29_

Além de especificar intervalos de portas a serem usados pelos seus clientes do Lync, você também deve criar políticas de Qualidade do serviço separadas que serão aplicadas aos computadores do cliente. (As políticas de Qualidade de serviço criadas para os servidores de Conferências, Aplicativos e Mediação não devem ser aplicadas aos computadores do cliente.) Essas informações aplicam-se apenas aos computadores que executam o cliente Lync 2013, o Windows 7 ou Windows 8.

O seguinte exemplo usa esse conjunto de intervalos de portas para criar uma política de áudio e uma política de vídeo:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de tráfego do cliente</th>
<th>Porta de início</th>
<th>Intervalo de portas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Áudio</p></td>
<td><p>50020</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Vídeo</p></td>
<td><p>58000</p></td>
<td><p>20</p></td>
</tr>
<tr class="odd">
<td><p>Compartilhamento de aplicativos</p></td>
<td><p>42000</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Transferência de arquivos</p></td>
<td><p>42020</p></td>
<td><p>20</p></td>
</tr>
</tbody>
</table>


Para criar uma política de áudio de Qualidade do Serviço em computadores com Windows 7 ou Windows 8, primeiro faça login em um computador que tenha instalado o Gerenciamento de Diretiva de Grupo. Abra o Gerenciamento de Diretiva de Grupo (clique em **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciamento de Diretiva de Grupo**) e execute o seguinte procedimento:

1.  No Gerenciamento de Diretiva de Grupo, localize o contêiner onde a nova política deve ser criada. Por exemplo, se todos os seus computadores do cliente estão localizados na OU denominada Clientes, então a nova política deve ser criada na OU Cliente.

2.  Clique com o botão direito no contêiner apropriado e em **Criar uma GPO neste domínio e fornecer um link para ele aqui**.

3.  Na caixa de diálogo **Nova GPO**, digite o nome do novo objeto de Diretiva de Grupo na caixa **Nome** (por exemplo **Áudio do Lync**) e clique em **OK**.

4.  Clique com o botão direito na política recém criada e clique em **Editar**.

5.  No Editor de Gerenciamento de Diretiva de Grupo, expanda **Configuração do computador**, **Diretivas**, **Configurações do Windows** e clique com o botão direito em **QoS baseado em política** e clique em **Criar nova política**.

6.  Na caixa de diálogo **QoS baseado em política** na página inicial, digite o nome da nova política (por exemplo, **Áudio do Lync**) na caixa **Nome**. Selecione **Especificar valor de DSCP** e defina o valor para **46**. Desmarque a caixa **Especificar taxa de aceleramento de saída** e clique em **Avançar**.

7.  Na próxima página, certifique-se de que **Todos os aplicativos** está selecionado e clique em **Avançar**. Essa configuração instrui a rede a buscar por todos os pacotes com uma marcação DSCP de 46, e não apenas pacotes criados por um aplicativo específico.

8.  Na terceira página, certifique-se de que **Qualquer endereço IP de origem** e **Qualquer endereço IP de destino** estão selecionados e clique em **Avançar**. Essas duas configurações garantem que os pacotes serão gerenciados independente do computador (endereço IP) que os enviou e que os receberá.

9.  Na página quatro, selecione **TCP e UDP** em **Selecionar que o protocolo desta política QoS seja aplicado a** na lista suspensa. TCP (Transmission Control Protocol) e UDP (User Datagram Protocol) são os dois protocolos de rede mais usados pelo Lync Server e seus aplicativos de cliente.

10. No cabeçalho **Especificar o número da porta de origem**, selecione **Deste número ou intervalo da porta de origem**. Na caixa oferecida, digite o intervalo de portas reservado para transmissões de áudio. Por exemplo, se você reservou as portas 50020 a 50039 para tráfedo de áudio, digite o intervalo de portas usando este formato: **50020:50039**. Clique em **Concluir**.

Após criar a política QoS para áudio, você deve criar uma segunda política para vídeo. Para criar uma política para vídeo, siga o mesmo procedimento básico executado para criar a política de áudio, fazendo as seguintes substituições:

  - Use um nome de política diferente (e exclusiva, como **Vídeo do Lync**).

  - Defina o valor de DSCP para **34**, em vez de 46. (Conforme destacado anteriormente, você não precisa usar o valor de DSCP 34; você apenas deve atribuir um valor de DSCP diferente daquele usado para áudio.)

  - Use o intervalo de portas configurado anteriormente para tráfego de vídeo. Por exemplo, se você reservou as portas 58000 a 58019 para vídeo, então defina o intervalo e portas desta forma: **58000:58019**.

Se decidir criar uma política para gerenciar o tráfego de compartilhamento de aplicativos, faça essas substituições:

  - Use um nome de política diferente (e exclusiva, como **Compartilhamento de aplicativos do Lync Server**).

  - Defina o valor de DSCP para **24**, em vez de 46. (Novamente, esse valor não precisa ser 24; apenas deve ser diferente dos valores de DSCP usados para áudio e vídeo.)

  - Use o intervalo de portas configurado anteriormente para tráfego de vídeo. Por exemplo, se você reservou as portas 42000 a 42019 para compartilhamento de aplicativos, então defina o intervalo e portas desta forma: **42000:42019**.

Para uma política de transferência de arquivo:

  - Use um nome de política diferente (e exclusivo, como **Transferências de arquivos do Lync Server**).

  - Defina o valor de DSCP para **14**. (Novamente, este valor não precisar ser 14; apenas deve ser um código DSCP exclusivo.)

  - Use o intervalo de portas configurado anteriormente para o aplicativo. Por exemplo, se você reservou as portas de 42020 a 42039 para compartilhamento de aplicativos, então defina o intervalo de portas assim: **42020:42039**.

As novas políticas criadas não serão aplicadas até que a Política de Grupos seja atualizada nos computadores do cliente. Embora a Política de Grupo seja atualizada periodicamente por conta própria, é possível aplicar uma atualização imediata executando o seguinte comando em cada computador em que a Política de Grupo precisa ser atualizada:

    Gpudate.exe /force

Este comando pode ser executado de qualquer janela de comando em execução com credenciais de administrador. Para executar uma janela de comando com credenciais de administrador, clique em **Iniciar**, clique com o botão direito em **Prompt de comandos** e depois em **Executar como administrador**.

Tenha em mente que essas políticas devem ser direcionadas aos seus computadores de cliente. Ela não devem ser aplicadas a servidores executando o Lync Server.

Para ajudar a garantir que os pacotes de rede sejam marcados com o valor DSCP apropriado, você também deve criar uma nova entrada no registro em cada computador, executando o seguinte procedimento:

1.  Clique em **Iniciar** e depois em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e pressione ENTER.

3.  No Editor do Registro, expanda **HKEY\_LOCAL\_MACHINE**, expanda **SYSTEM**, expanda **CurrentControlSet**, expanda **services**, e depois expanda **Tcpip**.

4.  Clique com o botão direito do mouse em **Tcpip**, vá até **Novo**, e clique em **Chave**. Depois de criar a nova chave de registro, digite **QoS** e pressione ENTER para renomear a chave.

5.  Clique com o botão direito do mouse em **QoS**, vá até **Novo**, e clique em **Valor da cadeia de caracteres**. Depois de criar o novo valor de registro, digite **Não usar NLA** e pressione ENTER para renomear o valor.

6.  Clique duas vezes em **Não usar NLA**. Na caixa de diálogo **Editar cadeia de caracteres**, digite **1** na caixa **Dados do valor** e clique em **OK**.

7.  Feche o Editor do Registro e reinicie o computador.

## Configurando a Qualidade do Serviço em computadores com diversos adaptadores de rede

Se o seu computador tem diversos adaptadores de rede, você ocasionalmente pode ter problemas em que os valores de DSCP são mostrados como 0x00 em vez de o valor configurado. Isso geralmente ocorrerá em computadores em que um ou mais adaptadores de rede não conseguem acessar o seu domínio do Active Directory (por exemplo, se esses adaptadores são usados para uma rede privada). Nestes casos, os valores de DSCP serão marcados para os adaptadores que podem acessar o domínio, mas não serão marcados para aqueles que não conseguem acessar o domínio.

Se desejar marcar os valores de DSCP para todos os adaptadores de rede em um computador, incluindo adaptadores que não têm acesso ao seu domínio, você precisará adicionar e configurar um valor no registro. Isso pode ser feito realizando o seguinte procedimento:

1.  Clique em **Iniciar** e depois em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e pressione ENTER.

3.  No Editor de Registro, expanda **HKEY\_LOCAL\_MACHINE**, expanda **SYSTEM**, expanda **CurrentControlSet**, expanda **services**, e depois expanda **Tcpip**.

4.  Se você não ver uma chave de registro rotulada **QoS**, clique com o botão direito em **Tcpip**, vá até **Novo**, e clique em **Chave**. Depois de criar a nova chave, digite **QoS** e pressione ENTER para renomear a chave.

5.  Clique com o botão direito do mouse em **QoS**, vá até **Novo**, e clique em **Valor da cadeia de caracteres**. Depois de criar o novo valor de registro, digite **Não usar NLA** e pressione ENTER para renomear o valor.

6.  Clique duas vezes em **Não usar NLA**. Na caixa de diálogo **Editar cadeia de caracteres**, digite **1** na caixa **Dados do valor** e clique em **OK**

Após criar e configurar o novo valor do registro, você precisará reiniciar o computador para as alterações serem aplicadas.

