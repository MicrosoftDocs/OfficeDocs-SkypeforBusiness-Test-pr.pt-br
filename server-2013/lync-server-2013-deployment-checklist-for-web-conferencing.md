---
title: Lista de verificação de implantação para webconferência
TOCTitle: Lista de verificação de implantação para webconferência
ms:assetid: 9908ebe0-e5d3-4920-b9b1-85021f7e69e9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205104(v=OCS.15)
ms:contentKeyID: 49307556
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de implantação para webconferência

 

_**Tópico modificado em:** 2015-03-09_

Como ocorre com a implantação de outros componentes do Lync Server 2013, a implantação da webconferência requer o uso do Construtor de Topologias para criar e publicar uma topologia que incorpora conferência.

## Sequência de implantação

É possível implantar conferência ao mesmo tempo em que a topologia inicial é implantada ou depois de implantar ao menos um Pool de Front-Ends ou Servidor Standard Edition.

## Processo de implantação de conferência

A tabela a seguir fornece uma visão geral das etapas necessárias para implantar a conferência em uma topologia existente.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Funções e associações de grupo</th>
<th>Documentação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Instalar prerrequisitos de hardware e software</strong></p></td>
<td><p>Conferências são executadas no Servidores Front-End em um Pool de Front-Ends e Servidores Standard Edition. Elas não têm requisitos de hardware ou software adicionais além do que é exigido para instalar esses servidores.</p>

> [!NOTE]  
> O Lync Server 2013 usa Office Web Apps e o Servidor Office Web Apps para lidar com o compartilhamento e renderização de apresentações do PowerPoint. Para obter informações sobre a instalação e configuração do Servidor Office Web Apps, consulte <a href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Configurando a integração com servidor de Office Web Apps e Lync Server 2013</a>.

</td>
<td><p>Domínio do usuário que é membro do grupo local de Administradores</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Hardware suportado para Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Suporte a software e à infraestrutura de servidor no Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Determinando seus requisitos de sistema para Lync Server 2013</a> na documentação Planejamento.</p>
<p><a href="lync-server-2013-technical-requirements-for-archiving.md">Requisitos técnicos de Arquivamento no Lync Server 2013</a> na documentação Planejamento.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Crie a topologia interna apropriada para dar suporte à conferência</strong></p></td>
<td><p>Execute Construtor de Topologias para adicionar a conferência à topologia e depois, publique a topologia.</p></td>
<td><p>Para definir a topologia, uma conta que é membro do grupo local de Usuários</p>
<p>Para publicar a topologia, uma conta que é membro do grupo de Admins. do Domínio e do grupo do RTCUniversalServerAdmins, e que tem permissões de controle total (ler/gravar/modificar) sobre o compartilhamento do arquivo a ser usado para o armazenamento de arquivos do Lync Server 2013 (de forma que o Construtor de Topologias possa configurar os DACLs requeridos)</p></td>
<td><p><a href="lync-server-2013-define-and-configure-a-topology-in-topology-builder.md">Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013</a> na documentação Implantação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configurar políticas e suporte de conferência</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para configurar a conferência.</p></td>
<td><p>Grupo RTCUniversalServerAdmins (apenas Windows PowerShell) ou designe usuários para [] ou a função de CSAdministrator</p></td>
<td><p><a href="lync-server-2013-conferencing-policies.md">Políticas de conferência no Lync Server 2013</a> na documentação Operações.</p></td>
</tr>
</tbody>
</table>


O Lync Server 2013 agora inclui a configuração **MaxUploadFileSizeMb**, que limita o tamanho dos arquivos que podem ser enviados durante uma reunião. O valor padrão dessa configuração é 500 MB. Você pode ajustar o **MaxUploadFileSizeMb** usando o cmdlet **Set-CsConferencingConfiguration**.

**MaxUploadFileSizeMb** não limita a configuração de upload de arquivo do Lync Web App. O limite de upload de tamanho de arquivo do Lync Web App é definido como aproximadamente 30MB e é controlado pelo arquivo IIS web.config: /DataCollabWeb/Int\[Ext\]/Handler/web.config. Para configurar o limite de upload de tamanho de arquivo do Lync Web App, atualize `maxRequestLength` e `maxAllowedContentLength` no arquivo web.config como mostrado abaixo.

    <system.web>
        <!-- 
            Since this handler is used to upload files to DMCU the request size (in kilobytes) 
            has to fit max allowed file size uploaded by LWA client.
            The timeout has to reflect the min client bandwidth. Timeout of 600 secs 
            and 512 Kbits of *client* bandwidth would result into aproximately 30 Mbytes 
            for LWA upload size limit.
        -->
          <httpRuntime maxRequestLength="500000" executionTimeout="600" />
    
    
    
                    <security>
                    <requestFiltering>
                               <requestLimits maxAllowedContentLength="524288000" />
                    </requestFiltering>
                    </security>

Você deve atualizar o arquivo web.config para cada Servidor Front-End.

