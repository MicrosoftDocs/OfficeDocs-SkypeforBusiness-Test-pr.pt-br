---
title: Exibir atualizações de software para dispositivos no Lync Server 2013
TOCTitle: Exibir atualizações de software para dispositivos no Lync Server 2013
ms:assetid: d2cca12b-ed43-4e1f-90ab-d14bca8b482c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182592(v=OCS.15)
ms:contentKeyID: 49308189
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir atualizações de software para dispositivos no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Com o Lync Server 2013, use o Serviço Web de Atualização de Dispositivos para visualizar e gerenciar atualizações de software para os dispositivos da sua organização. Essas atualizações estão disponíveis em arquivos .cab (gabinete) no site Microsoft Support em [http://go.microsoft.com/fwlink/?linkid=204091\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=204091%26clcid=0x416). Depois de baixar o arquivo .cab, execute o cmdlet **Import-CSdeviceUpdate** para importar as regras de atualização de dispositivos do arquivo .cab. Para obter detalhes sobre o cmdlet **Import-CSdeviceUpdate**, consulte [Import-CsDeviceUpdate](https://docs.microsoft.com/en-us/powershell/module/skype/Import-CsDeviceUpdate), na documentação do Shell de Gerenciamento do Lync Server.


> [!TIP]
> Antes de implantar uma nova atualização em sua organização, verifique se ele funciona corretamente em um dispositivo de teste.



## Para exibir as atualizações de software para dispositivos UC

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  No site Microsoft Support em [http://go.microsoft.com/fwlink/?linkid=204091\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=204091%26clcid=0x416), baixe o arquivo .cab para um local em um computador com Lync Server 2013 (por exemplo, C:\\Updates\\UCUpdates.cab).

3.  Importe as regras de atualização de dispositivo do arquivo C:\\Updates\\UCUpdates.cab executando um dos seguintes cmdlets:
    
      - Se o arquivo. cab estiver localizado no mesmo computador que está executando o serviço a ser atualizado (serviço: Redmond-websvc-2), execute o seguinte cmdlet:
        
            Import-CsDeviceUpdate -Identity service:Redmond-websvc-2 -FileName C:\Updates\UCUpdates.cab
    
      - Se o arquivo. cab estiver localizado em um computador diferente do que está executando o serviço a ser atualizado (serviço: Redmond-websvc-3), execute o seguinte cmdlet:
        
            Import-CsDeviceUpdate -Identity service:Redmond-websvc-3 -ByteInput C:\Updates\UCUpdates.cab

4.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

5.  Na barra de navegação esquerda, clique em **Cliente** e em **Atualização de Dispositivo**.

6.  Na página **Atualização de Dispositivo**, clique em uma atualização na lista e execute um dos seguintes procedimentos:
    
      - **Cancelar uma atualização pendente.** Para impedir que a atualização selecionada seja implantada nos dispositivos de sua organização, clique no menu **Ação** e clique em **Cancelar atualizações pendentes**.
    
      - **Aprovar uma atualização.** Para permitir que a atualização selecionada seja implantada em dispositivos de sua organização, clique no menu **Ação** e, em seguida, clique **Aprovar**.
    
      - **Restaurar uma atualização.** Para permitir que uma atualização aprovada anteriormente seja implantada nos dispositivos de sua organização, clique no menu **Ação** e, em seguida, clique **Restaurar**.

## Consulte Também

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

