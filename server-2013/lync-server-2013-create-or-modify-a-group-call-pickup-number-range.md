---
title: Criar ou modificar um intervalo numérico de recebimento de chamadas em grupo
TOCTitle: Criar ou modificar um intervalo numérico de recebimento de chamadas em grupo
ms:assetid: 4b442b98-df6b-4e50-8254-b3be9cde21dd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945627(v=OCS.15)
ms:contentKeyID: 52057601
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um intervalo numérico de recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2013-01-30_

Utilize o procedimento a seguir para criar ou modificar o intervalo de números de um grupo de atendimento de chamadas na tabela de órbita de estacionamento de chamadas.

> [!NOTE]  
> Você precisa utilizar Shell de Gerenciamento do Lync Server para criar, modificar, remover e visualizar intervalos de números de atendimento de chamadas em grupo na tabela de órbita de estacionamento de chamadas. Intervalos de números de atendimento de chamadas em grupo não estão disponíveis em Painel de Controle do Lync Server.

> [!IMPORTANT]  
> É preciso atribuir ao intervalo de números de grupo de atendimento de chamadas o tipo GroupPickup. Usuários são habilitados para o atendimento de chamadas em grupo somente se o número de grupo a que foram atribuídos for do tipo GroupPickup.

Os intervalos de números de grupo de atendimento de chamadas precisam estar de acordo com as regras a seguir:

  - O número inicial do intervalo deve ser menor ou igual ao número final.

  - O valor do número inicial do intervalo deve ter o mesmo comprimento que o número final do intervalo.

  - O intervalo de números precisa ser exclusivo. Esse intervalo não pode se sobrepor a nenhum outro intervalo.

  - Se o intervalo de números começar com o caractere \* ou \#, o intervalo deverá ser maior do que 100.

  - Valores válidos: precisa corresponder à cadeia de caracteres de expressão regular (\[\\\*|\#\]?\[1-9\]\\d{0,7})|(\[1-9\]\\d{0,8}). Isso significa que o valor deve ser uma cadeia de caracteres começando com o caractere \* ou \# ou um número de 1 a 9 (o primeiro caractere não pode ser zero). Se o primeiro caractere é \* ou \#, o caractere seguinte deve ser um número de 1 a 9 (não pode ser zero). Os caracteres subsequentes podem ser qualquer número de 0 a 9 até sete caracteres adicionais (por exemplo, "\#6000", "\*92000", "\*95551212" e "915551212"). Se o primeiro caractere não é \* ou \#, deve ser um número de 1 a 9 (não pode ser zero), seguido por oito caracteres, cada um com número de 0 a 9 (por exemplo: "915551212", "41212", "300").

## Para criar ou modificar um intervalo de grupo de atendimento de chamadas

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use o **New-CsCallParkOrbit** para criar um novo intervalo de números de grupo de atendimento de chamadas. Use o **Set-CsCallParkOrbit** para modificar um intervalo existente de números de atendimento de chamadas.
    
    Na linha de comando, execute:
    
        New-CsCallParkOrbit -Identity <name of call pickup group range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application> -Type GroupPickup
    
    Por exemplo:
    
        New-CsCallParkOrbit -Identity "Redmond call pickup" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1 -Type GroupPickup
    
    O exemplo a seguir mostra como trocar um intervalo de números de órbitas de estacionamento de chamadas para grupos de atendimento de chamadas.
    
        Set-CsCallParkOrbit -Identity "Redmond call pickup" -Type GroupPickup
    
    > [!IMPORTANT]  
    > Use esse cmdlet para mudar o tipo atribuído aos intervalos de números somente se você tiver especificado inicialmente o tipo incorreto e somente caso o intervalo de grupo ainda não esteja em uso. Se você alterar o intervalo de números de CallPark para GroupPickup ou vice-versa e o intervalo de números já estiver em uso, o estacionamento de chamada ou o atendimento de chamada em grupo irá parar de funcionar para aquele intervalo de números. Por exemplo, se você alterar um intervalo de números de CallPark para GroupPick, o Aplicativo de Estacionamento de Chamada não poderá mais utilizar aquele intervalo de órbitas para estacionar chamadas.

## Consulte Também

#### Tarefas

[Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013](lync-server-2013-delete-a-call-park-orbit-range.md)  

#### Outros Recursos

[New-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCallParkOrbit)  
[Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit)

