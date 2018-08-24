---
title: "Configurando uma política de Qual. de Serviço (QoS) p/ seus serv. de borda A/V"
TOCTitle: "Configurando uma política de Qual. de Serviço (QoS) p/ seus serv. de borda A/V"
ms:assetid: 119ee1f5-45b9-40ba-98e5-c694dd2fc5c2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204681(v=OCS.15)
ms:contentKeyID: 49305924
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando uma política de Qualidade de Serviço (QoS) para seus servidores de borda A/V

 

_**Tópico modificado em:** 2012-10-19_

Além de criar políticas de QoS para seus servidores de Conferências, Aplicativos e Mediação, você também deve criar políticas de áudio e vídeo para o lado interno dos seus servidores de borda de A/V. No entanto, as políticas usadas em seus servidores de Borda são diferentes das políticas usadas em seus servidores de Conferências, Aplicativos e Mediação. Para os servidores de Conferências, Aplicativos e Mediação, você especificou um intervalo de portas de origem; com servidores de Borda, é necessário especificar um intervalo de portas de destino. Por isso não é possível simplesmente aplicar as políticas de QoS do servidor de Conferências, Aplicativos e Mediação em seus servidores de Borda: essas políticas simplesmente não funcionarão. Em vez disso, você deve criar novas políticas e aplicá-las somente aos seus servidores de Borda.

O procedimento a seguir descreve o processo para criar objetos de Política de Grupo do Active Directory que podem ser usados para gerenciar a Qualidade de Serviço em Servidores de Borda. É possível, é claro, que seus servidores de Borda sejam servidores autônomos que não possuem contas do Active Directory. Neste caso, você pode usar uma Política de Grupo local em vez da Política de Grupo do Active Directory: a única diferença é que você deve criar essas políticas locais usando o Editor de Políticas de Grupo Local e deve criar individualmente o mesmo conjunto de políticas em cada Servidor de Borda. Para iniciar o Editor de Políticas de Grupo Local em um servidor de Borda, faça o seguinte:

1.  Clique em **Iniciar** e em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **gpedit.msc** e pressione ENTER.

Se estiver criando políticas com base no Active Directory, você deve fazer logon em um computador em que o Gerenciamento de Política de Grupo tenha sido instalado. Neste caso, abra o Gerenciamento de Política de Grupo (clique em **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciamento de Política de Grupo**) e conclua as seguintes etapas:

1.  No Gerenciamento de Política de Grupo, localize o contêiner em que a nova política deve ser criada. Por exemplo, se todos os seus computadores Lync Server estiverem localizados em uma UO chamada Lync Server, a nova política deve ser criada na UO Lync Server.

2.  Clique com o botão direito no contêiner adequado e clique em **Criar um GPO neste domínio e fornecer um link para ele aqui**.

3.  Na caixa de diálogo **Novo GPO**, digite um nome para o novo objeto de Política de Grupo na caixa **Nome** (por exemplo, **Áudio do Lync Server**) e clique em **OK**.

4.  Clique com o botão direito na política recém criada e clique em **Editar**.

A partir daqui o processo é idêntico, independente de você estar criando uma política do Active Directory ou uma política local:

1.  No Editor do Gerenciamento de Política de Grupo ou no Editor de Política de Grupo Local, expanda **Configuração do Computador**, **Políticas**, **Configurações do Windows**, clique com o botão direito em **QoS baseada em política** e clique em **Criar nova política**.

2.  Na caixa de diálogo **QoS baseada em política**, na página inicial, digite um nome para a nova política (por exemplo, **Áudio do Lync Server**) na caixa **Nome**. Selecione **Especificar valor de DSCP** e defina o valor como **46**. Deixe a opção **Especificar Taxa de Aceleração de Saída** desmarcada e clique em **Avançar**.

3.  Na página seguinte, certifique-se de que a opção **Todos os aplicativos** esteja selecionada e clique em **Avançar**. Esta configuração instrui a rede a procurar todos os pacotes com uma marcação de DSCP igual a 46, não somente pacotes criados por um aplicativo específico.

4.  Na terceira página, certifique-se de que ambas as opções **Qualquer endereço IP de origem** e **Qualquer endereço IP de destino** estejam selecionadas e clique em **Avançar**. Essas duas configurações garantem que os pacotes serão gerenciados independente de qual computador (endereço IP) tenha os enviado e de qual computador (endereço IP) os receberá.

5.  Na página quatro, selecione **TCP e UDP** na lista suspensa **Selecione o protocolo ao qual esta política de QoS se aplica**. TCP (Transmission Control Protocol) e UDP (User Datagram Protocol) são os dois protocolos de rede mais comumente usados pelo Lync Server e seus aplicativos clientes.

6.  Sob o cabeçalho **Especifique o número da porta de destino**, selecione **A partir desta porta de destino ou intervalo**. Na caixa de texto que acompanha, digite o intervalo de portas reservado para transmissões de áudio. Por exemplo, se você reservou as portas 49152 até as portas 57500 para o tráfego de áudio, insira o intervalo de portas usando este formato: **49152:57500**. Clique em **Concluir**.

Depois de criar a política de QoS para o tráfego de áudio, você deve criar uma segunda política para o tráfego de vídeo. Para criar uma política para vídeo, siga o mesmo procedimento básico da criação da política de áudio, fazendo as seguintes substituições:

  - Use um nome de política diferente (e único) (por exemplo, **Vídeo do Lync Server**).

  - Defina o valor do DSCP como **34** em vez de 46 (observe que você não precisa usar o valor 34 para o DSCP. O único requisito é usar para o vídeo um valor de DSCP diferente do valor usado para o áudio).

  - Use o intervalo de portas configurado anteriormente para o tráfego de vídeo. Por exemplo, se você reservou as portas 57501 a 65535 para vídeo, defina o intervalo de portas como: **57501:65535**. Novamente, isso deve ser configurado como intervalo de portas de destino.

Se você decidir criar uma política para gerenciar o tráfego de compartilhamento de aplicativos, deve criar uma terceira política, fazendo as seguintes substituições:

  - Use um nome de política diferente (e único) (por exemplo, **Compartilhamento de Aplicativos do Lync Server**).

  - Defina o valor do DSCP como **24** em vez de 46 (novamente, não é necessário usar o valor 24 para o DSCP. O único requisito é usar para o compartilhamento de aplicativos um valor de DSCP diferente do valor usado para áudio e vídeo).

  - Use o intervalo de portas configurado anteriormente para o tráfego de vídeo. Por exemplo, se você reservou as portas 40803 a 49151 para o compartilhamento de aplicativos, defina o intervalo de portas como: **40803:49151**.

As novas políticas criadas não terão efeito até que a Política de Grupo tenha sido atualizada nos servidores de Borda. Embora a Política de Grupo seja atualizada periodicamente sozinha, você pode forçar uma atualização imediata executando o comando a seguir em cada computador em que for necessário atualizar a Política de Grupo:

    Gpudate.exe /force

Este comando pode ser executado de dentro do Lync Server ou a partir de qualquer janela de comando que esteja sendo executada sob credenciais de administrador. Para executar uma janela de comando sob credenciais de administrador, clique em **Iniciar**, clique com o botão direito em **Prompt de Comando** e clique em **Executar como administrador**. Observe que pode ser necessário reiniciar o servidor de Borda mesmo depois de executar o arquivo Gpudate.exe.

Para ajudar a garantir que os pacotes de rede sejam marcados com o valore DSCP correto, você também deve criar uma nova entrada de registro em cada computador, concluindo o procedimento a seguir:

1.  Clique em **Iniciar** e em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e pressione ENTER.

3.  No Editor do Registro, expanda **HKEY\_LOCAL\_MACHINE**, **SYSTEM**, **CurrentControlSet**, **services** e **Tcpip**.

4.  Clique com o botão direito em **Tcpip**, aponte para **Novo** e clique em **Chave**. Depois de criar a nova chave de registro, digite **QoS** e pressione ENTER para renomear a chave.

5.  Clique com o botão direito em **QoS**, aponte para **Novo** e clique em **Valor da Sequência**. Depois de criar o novo valor do registro, digite **Não usar NLA** e pressione ENTER para renomear o valor.

6.  Dê um duplo clique em **Não usar NLA**. Na caixa de diálogo **Editar Sequência**, digite **1** na caixa **Dados de valor** e clique em **OK**.

7.  Feche o Editor do Registro e reinicie o computador.

