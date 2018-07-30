---
title: 'Lync Server 2013: Configurando uma política de Qualidade de Serviço para seus servidores de Conferência, de Aplicativo e de Mediação'
TOCTitle: Configurando uma política de Qualidade de Serviço para seus servidores de Conferência, de Aplicativo e de Mediação
ms:assetid: 8adcbbc5-c9f5-476d-ab7f-72e61859cacf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205076(v=OCS.15)
ms:contentKeyID: 49307402
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando uma política de Qualidade de Serviço no Lync Server 2013 para seus servidores de Conferência, de Aplicativo e de Mediação

 

_**Tópico modificado em:** 2014-06-23_

Configurar intervalos de porta facilita o uso da Qualidade de Serviço, garantindo que todo o tráfego de um tipo especificado (por exemplo, todo o tráfego de áudio) percorra o mesmo conjunto de portas. Isso facilita para o sistema identificar e marcar um dado pacote: se a porta 49152 estiver reservada para tráfego de áudio, então qualquer pacote que passar pela porta 49152 poderá ser marcado com um código DSCP indicando que é um pacote de áudio. Por sua vez, isso permite que os roteadores identifiquem o pacote como um pacote de áudio, e forneçam a ele uma prioridade maior que a de pacotes não marcados (como pacotes usados para copiar um arquivo de um servidor a outro).

No entanto, restringir simplesmente um conjunto de portas para um tipo de tráfego específico não faz com que os pacotes que viajam através dessas portas sejam marcados com o código DSCP apropriado. Além de definir o intervalo de portas, é necessário criar políticas de Qualidade de Serviço que especificam que o código DSCP seja associado com cada intervalo de porta. Para o Microsoft Lync Server 2013 isso geralmente significa criar duas políticas: uma para áudio e uma para vídeo.

As políticas de Qualidade de Serviço são criadas e gerenciadas de forma mais fácil usando uma Política de Grupo. (Essas mesmas políticas podem também ser criadas usando políticas de segurança local. No entanto, isso exige que você repita o mesmo procedimento em todos os computadores). Seu conjunto inicial de políticas de QoS (uma para áudio e uma para vídeo) deve ser aplicado apenas a computadores do Lync Server executando os serviços do servidor de Conferência, servidor de Aplicativos e/ou servidor de Mediação. Se todos esses computadores estiverem localizados no mesmo OU do Active Directory, então você pode simplesmente atribuir um novo objeto de Política de Grupo (GPO) a esse OU. Como alternativa, você pode fazer outro procedimento para abordar a nova política para os computadores especificados; por exemplo, você pode colocar os computadores apropriados em um grupo de segurança, depois usar a filtragem de segurança de Política de Grupo para aplicar a GPO apenas a esse grupo de segurança.

Para criar uma política de Qualidade de Serviço para gerenciar áudio, faça logon em um computador onde o Gerenciamento de Política de Grupo foi instalado. Abra o Gerenciamento de Política de Grupo (clique em **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciamento de Política de Grupo** ) e siga o próximo procedimento.

1.  No Gerenciamento de Política de Grupo, localize o contêiner onde a nova política deve ser criada. Por exemplo, se todos os seus computadores do Lync Server estiverem em um OU chamado Lync Server, então a nova política deverá ser criada no OU do Lync Server.

2.  Clique com o botão direito no contêiner apropriado e depois clique em **Criar um GPO neste domínio e fornecer um link para ele aqui**.

3.  Na caixa de diálogo **Novo GPO**, digite o nome para o novo objeto de Política de Grupo na caixa **Nome** (por exemplo, **QoS do Lync Server** e clique em **OK**.

4.  Clique com o botão direito na política recém criada e depois clique em **Editar**.

5.  No Editor de Gerenciamento de Política de Grupo, expanda **Configuração do computador**, expanda **Políticas**, expanda **Configurações do Windows**, clique com o botão direito em **QoS baseado em política**, e depois clique em **Criar nova política**.

6.  Na caixa de diálogo **QoS baseado em política**, na página de abertura, digite um nome para a nova política (p.ex., **QoS do Lync Server** ) na caixa **Nome**. Selecione **Especificar valor DSCP** e defina o valor para **46**. Mantenha **Especificar Taxa de Aceleração de Saída** sem selecionar e depois clique em **Avançar**.

7.  Na página seguinte, certifique-se de selecionar **Todos os Aplicativos** e depois clique em **Avançar**. Isso garante que todos os aplicativos compararão os pacotes da porta especificada com o código DSCP especificado.

8.  Na terceira página, certifique-se de que **Qualquer endereço IP de origem e Qualquer endereço IP de destino** estão selecionados e depois clique em **Avançar**. Essas duas configurações garantem que os pacotes serão gerenciados independentemente de qual computador (endereço IP) enviar esses pacotes e qual computador (endereço IP) os receberá.

9.  Na página quatro, selecione **TCP e UDP** na lista suspensa em **Selecionar o protocolo ao qual esta diretiva de QoS se aplica**. TCP (Transmission Control Protocol) e UDP (User Datagram Protocol) são os dois protocolos de rede mais comuns usados pelo Lync Server e seus aplicativos cliente.

10. No cabeçalho **Especifique o número da porta de origem**, selecione **Desta porta ou intervalo de origem**. Na caixa de texto acompanhante, digite o intervalo de porta reservado para transmissões de áudio. Por exemplo, se você reservou as portas de 49152 a 57500 para tráfego de aúdio, insira o intervalo de porta usando esse formato: **49152:57500**. Clique em **Concluir**.

> [!NOTE]  
> O valor DSCP de 46 é de certa forma arbitrário: embora DSCP 46 seja usado com frequência para marcar pacotes de áudio, você não precisa usar o DSCP 46 para comunicação de áudio. Se já tiver implementado QoS e estiver usando um código DSCP diferente para áudio (por exemplo, DSCP 40), então você deverá configurar sua política de Qualidade de Serviço para usar o mesmo código (ou seja, 40 para áudio). Se só agora você estiver implementado a Qualidade de Serviço, recomendamos que você use DSCP 46 para áudio, simplesmente porque este valor é o mais comumente usado para marcar pacotes de áudio.

Após criar a política QoS para tráfego de áudio, você deverá criar uma segunda política para tráfego de vídeo (e, opcionalmente, uma terceira para gerenciar tráfego de compartilhamento de aplicativos). Para criar uma política para vídeo, siga o mesmo procedimento básico para criar política de áudio, fazendo essas substituições:

  - Use um nome de política diferente (e único, por exemplo, **Vídeo do Lync Server**.

  - Defina o valor DSCP para **34** em vez de 46. (Observe que não é necessário usar um valor DSCP de 34). A única exigência é usar um valor DSCP diferente para vídeo e para áudio).

  - Use o intervalo de porta anteriormente configurado para tráfego de vídeo. Por exemplo, se tiver reservado as portas de 57501 a 65535 para vídeo, então defina o intervalo de porta para: **57501:65535**.

Se decidir criar uma política para gerenciar o tráfego de compartilhamento de aplicativos, você deverá criar uma terceira política, fazendo as seguintes substituições:

  - Use um nome de política diferente (e único, por exemplo, **Compartilhamento de aplicativos do Lync Server**.

  - Defina o valor DSCP para **24** em vez de 46. (Novamente, não é necessário usar um valor DSCP de 24). A única exigência é usar um valor DSCP diferente para o compartilhamento de aplicativos, áudio e vídeo).

  - Use o intervalo de porta anteriormente configurado para tráfego de vídeo. Por exemplo, se tiver reservado portas de 40803 a 49151 para compartilhamento de aplicativos, então defina o intervalo de porta para: **40803:49151**.

As novas políticas criadas não entrarão em vigor até que a Política de Grupo tenha sido atualizada em seus computadores do Lync Server. Embora a Política de Grupo seja atualizada periodicamente sozinha, você pode forçar uma atualização imediata executando o seguinte comando em cada computador onde a Política de Grupo precise ser atualizada.

    Gpupdate.exe /force

Esse comando pode ser executado de dentro do Shell de Gerenciamento do Lync Server ou de qualquer janela de comando que esteja sendo executada sob credenciais de administrador. Para executar uma janela de comando sob credenciais de administrador, clique em **Iniciar**, clique com o botão direito em **Prompt de comando**, e depois em **Executar como administrador**.

Para verificar se as novas políticas de QoS foram aplicadas, faça o seguinte:

1.  Em um computador do Lync Server, clique em **Iniciar** e depois em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e depois pressione ENTER.

3.  No Editor do Registro, expanda **Computador**, expanda **HKEY\_LOCAL\_MACHINE**, expanda **SOFTWARE**, expanda **Policies**, expanda **Microsoft**, expanda **Windows**, e depois clique em **QoS**. Em **QoS**, você deverá ver chaves de registro para cada política de QoS criada. Por exemplo, se você criou duas novas políticas (uma chamada QoS de Áudio do Lync Server e a outra chamada QoS de Vídeo do Lync Server), você deverá registrar entradas para QoS de Áudio do Lync Server e QoS de Vídeo do Lync Server.

Para ajudar a garantir que os pacotes de rede sejam marcados com o valor DSCP apropriado, você deverá criar também uma nova entrada de registro em cada computador, executando o procedimento a seguir:

1.  Clique em **Iniciar** e depois em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e depois pressione ENTER.

3.  No Editor do Registro, expanda **HKEY\_LOCAL\_MACHINE**, expanda **SYSTEM**, expanda **CurrentControlSet**, expanda **services**, e depois expanda **Tcpip**.

4.  Clique com o botão direito do mouse em **Tcpip**, aponte para **Novo** e depois clique em **Sim**. Depois que uma nova chave de registro for criada, digite **QoS** e pressione ENTER para renomear a chave.

5.  Clique com o botão direito do mouse em **QoS**, aponte para **Novo** e depois clique em **Valor da Cadeia de Caracteres**. Depois que um novo valor de registro for criado, digite **Não usar NLA** e pressione ENTER para renomear o valor.

6.  Clique duas vezes em **Não usar NLA**. Na caixa de diálogo **Editar Cadeia de Caracteres**, digite **1** na caixa **Dados do valor** e depois clique em **OK**.

7.  Feche o Editor do Registro e reinicie seu computador.

