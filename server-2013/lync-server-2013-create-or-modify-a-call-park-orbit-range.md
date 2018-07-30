---
title: 'Lync Server 2013: Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas'
TOCTitle: Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas
ms:assetid: 549ec118-eee5-4333-9416-80929ec057e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398361(v=OCS.15)
ms:contentKeyID: 49306737
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Utilize um dos seguintes procedimentos para criar ou modificar um intervalo de órbitas de estacionamento de chamada.

## Para usar o Painel de Controle do Lync Server para criar ou modificar um novo intervalo numérico para o estacionamento de chamada

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Recursos de Voz** e em **Estacionamento de Chamada(Call Park)** .

4.  Na página **Estacionamento de Chamada** , execute um dos seguintes procedimentos:
    
      - Para criar um novo intervalo de órbitas, clique em **Novo** . Em **Nome** , digite um nome de identificação para esse intervalo de números.
        
        > [!NOTE]  
        > Após confirmar o intervalo de órbitas do banco de dados, não será possível alterar esse nome.    
      - Para modificar um intervalo de órbitas existente, digite todo ou parte do nome do intervalo de órbitas no campo de pesquisa. Na lista de resultados de órbitas, clique na órbita que desejar, clique em **Editar** e clique em **Mostrar detalhes** .

5.  No primeiro campo do **Intervalo numérico** , digite o número inicial do intervalo de extensões desta órbita de estacionamento de chamada e, no segundo campo **Intervalo numérico** , digite o número final do intervalo.
    
    > [!NOTE]  
    > <ul>    <li><p>O número inicial do intervalo deve ser menor ou igual ao número final.</p></li>    <li><p>O valor do número inicial do intervalo deve ter o mesmo comprimento que o número final do intervalo.</p></li>    
> <li><p>O intervalo de órbita deve ser exclusivo. Este intervalo não pode sobrepor outro intervalo.</p></li>    
> <li><p>Se o intervalo de órbita começa com o caractere * ou #, o intervalo deve ser maior que 100.</p></li>    
> 
> <li><p>Valores válidos: Deve corresponder a cadeia de caracteres de expressão regular ([\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). Isto significa que o valor deve ser uma cadeia de caracteres começando com o caractere * ou # ou um número de 1 a 9 (o primeiro caractere não pode ser zero). Se o primeiro caractere é * ou #, o seguinte caractere deve ser um número de 1 a 9 (não pode ser zero). Os caracteres subsequentes podem ser qualquer número de 0 a 9 até sete caracteres adicionais (por exemplo, &quot;#6000&quot;, &quot;*92000&quot;, &quot;*95551212&quot; e &quot;915551212&quot;). Se o primeiro caractere não é * ou #, deve ser um número de 1 a 9 (não pode ser zero), seguido por oito caracteres, cada um com número de 0 a 9 (por exemplo: &quot;915551212&quot;, &quot;41212&quot;, &quot;300&quot;).</p></li>    
> 
> 
> <li><p>Você não deve ter mais do que um total de 50.000 órbitas por pool. Cada intervalo de órbita geralmente possui 100 ou menos órbitas, mas pode ser muito maior contanto que inclua menos do que 10.000 órbitas. Por exemplo, ao invés de especificar um número inicial de &quot;7000000&quot; e um número final de &quot;8000000,&quot; considere especificar um número inicial de &quot;7000000&quot; e um número final de &quot;7000100.&quot;</p></li>    </ul>


6.  No **FQDN do servidor de destino** , clique no nome de domínio totalmente qualificado (FQDN) ou ID de serviço do serviço do aplicativo que hospeda o Aplicativo de Estacionamento de Chamada. Todas as chamadas estacionadas em números dentro do intervalo especificado pelo número inicial e número final do intervalo de órbita serão direcionadas para este servidor ou pool.

7.  Clique em **Confirmar** .

## Para usar o Windows PowerShell para criar ou modificar um novo intervalo numérico para o estacionamento de chamada

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use o **New-CsCallParkOrbit** para criar um novo intervalo de números de órbitas. Use o **Set-CsCallParkOrbit** para modificar um intervalo de números de órbitas de estacionamento de chamada existente.
    
    Na linha de comando, execute:
    
        New-CsCallParkOrbit -Identity <name of orbit range> -NumberRangeStart <first number in orbit range> -NumberRangeEnd <last number in orbit range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application>
    
    Por exemplo:
    
        New-CsCallParkOrbit -Identity "Redmond orbit 1" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1
    
    O seguinte exemplo mostra como modificar os números em intervalo de órbitas existente
    
        Set-CsCallParkOrbit -Identity "Redmond orbit 1" -NumberRangeStart 500 -NumberRangeEnd 699

## Consulte Também

#### Tarefas

[Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013](lync-server-2013-delete-a-call-park-orbit-range.md)  

#### Outros Recursos

[New-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCallParkOrbit)  
[Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit)

