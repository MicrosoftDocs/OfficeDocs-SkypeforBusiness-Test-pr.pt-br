---
title: Configurar clientes para migração
TOCTitle: Configurar clientes para migração
ms:assetid: 8f17862b-d9d1-47f6-b248-51f4710f5030
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688130(v=OCS.15)
ms:contentKeyID: 49886308
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar clientes para migração

 

_**Tópico modificado em:** 2016-12-08_

Este tópico contém as etapas recomendadas de implantação de cliente que devem ser executadas antes de migrar para o Lync Server 2013. Essas alterações de configuração devem ser feitas no Office Communications Server 2007 R2. É muito importante que essas etapas sejam executadas antes da migração. Para detalhes, consulte [Planejando clientes e dispositivos no Lync Server 2013](lync-server-2013-planning-for-clients-and-devices.md).

## Para configurar clientes antes da migração

1.  Implante o servidor, cliente e atualizações de dispositivo (hotfixes) do Office Communications Server 2007 R2 mais recentes.
    
      - [Aplicar atualizações do Office Communications Server 2007 R2](apply-office-communications-server-2007-r2-updates.md)
    
      - [Descrição do pacote de atualização cumulativa para o Communicator 2007 R2](http://go.microsoft.com/fwlink/p/?linkid=335808)
    
      - [Como obter atualizações de software para dispositivos](http://go.microsoft.com/fwlink/?linkid=335809)

2.  No Office Communications Server 2007 R2, use a Filtragem de Versão de Cliente para permitir que somente clientes do Office Communications Server 2007 R2 com as atualizações mais recentes instaladas possam entrar.

3.  No Office Communications Server 2007 R2, use a Filtragem de Versão de Cliente para bloquear a entrada de clientes do Lync Server 2013. Siga as etapas descritas em **Como Configurar a Filtragem de Versão de Cliente** em [http://go.microsoft.com/fwlink/?linkid=202488\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=202488%26clcid=0x416) para adicionar os filtros de versão listados na tabela a seguir. Para cada filtro de versão, atribua a ação **Bloquear**.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Cliente</th>
    <th>Cabeçalho do agente do usuário</th>
    <th>Versão</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Lync 2013</p></td>
    <td><p>OC</p></td>
    <td><p>15.*.*.*</p></td>
    </tr>
    <tr class="even">
    <td><p>Lync Web App</p></td>
    <td><p>CWA</p></td>
    <td><p>5.*.*.*</p></td>
    </tr>
    <tr class="odd">
    <td><p>Lync Phone Edition</p></td>
    <td><p>OCPhone</p></td>
    <td><p>4.*.*.*</p></td>
    </tr>
    </tbody>
    </table>

