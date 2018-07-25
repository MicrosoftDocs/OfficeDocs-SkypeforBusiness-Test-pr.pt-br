---
title: 'Lync Server 2013: Etapas para preparar e implantar o ambiente híbrido do Lync Server'
TOCTitle: Etapas para preparar e implantar o ambiente híbrido do Lync Server 2013
ms:assetid: a50d4f7b-63f4-4663-af63-56ca87e4e3e7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205157(v=OCS.15)
ms:contentKeyID: 49307693
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Etapas para preparar e implantar o ambiente híbrido do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A tabela a seguir lista as etapas necessárias para preparar o seu ambiente para uma implantação híbrida com Microsoft Lync Online e o Microsoft Office 365.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Concluído?</th>
<th>Etapa</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Crie uma conta de inquilino para o Office 365 e habilite o Lync Online</p></td>
<td><p>Saiba mais sobre o Office 365 e o Lync Online em <a href="http://go.microsoft.com/fwlink/p/?linkid=254980">Office 365</a>.</p>
<p>Para se certificar de que seu ambiente está pronto para o Office 365, consulte os <a href="http://go.microsoft.com/fwlink/p/?linkid=401408">Requisitos do Sistema</a>.</p>
<p>Para detalhes sobre como configurar o Office 365, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=254982">Introdução ao Office 365</a> e <a href="http://go.microsoft.com/fwlink/p/?linkid=254979">Como configurar o Office 365</a>.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Adicionar seu domínio e verificar quem é o proprietário</p></td>
<td><p>Seu domínio também é mencionado algumas vezes como seu <em>domínio personalizado</em> . Você precisa acrescentar seu domínio ao seu inquilino do Office 365, e então seguir as etapas para validar o domínio com o Office 365. Isso é feito para confirmar que você é o proprietário do domínio.</p>
<p>Para adicionar seu domínio ao locatário do Office 365, siga as etapas descritas em <a href="http://go.microsoft.com/fwlink/p/?linkid=254983">Como adicionar seu domínio ao Office 365</a>.</p>
<p>Complete todas as etapas em cada seção do tópico, incluindo &quot;Editar registros DNS para os seus serviços de Office 365.&quot;</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Verificar a prontidão do ambiente</p></td>
<td><p>Você pode usar o Assistente de Configuração do Office 365 para ajudá-lo a implantar o Office 365. Para mais informações, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=254985">Use o Assistente de Configuração para determinar a prontidão do Office 365</a>.</p>
<p>Para mais detalhes sobre como usar a ferramenta e implantar o Office 365, consulte o <a href="http://go.microsoft.com/fwlink/p/?linkid=257337">Guia de implantação do Office 365</a>.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Preparar-se para sincronização do Active Directory</p></td>
<td><p>A sincronização do Active Directory mantém o seu Active Directory local continuamente sincronizado com o Office 365. Isso permite que você crie versões sincronizadas de cada grupo e conta de usuário, e também habilita a sincronização de lista de endereços globais (GAL) a partir do seu ambiente local do Microsoft Exchange Server para Microsoft Exchange Online.</p>

> [!IMPORTANT]  
> Você precisará configurar as contas AD para todos os usuários do Lync em sua organização entre as implantações do Lync no local e online, mesmo se os usuários não forem movidos para o Lync Online. Se você não sincronizar todos os usuários, a comunicação entre os usuários online e locais em sua organização pode não funcionar como o esperado.

<p>Para preparar seu ambiente para sincronização Active Directory, siga as etapas descritas em <a href="http://go.microsoft.com/fwlink/p/?linkid=254988">Sincronização de diretório: Roteiro</a>, incluindo configuração de logon único.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Criar certificados para Serviços de Federação do Active Directory (AD FS)</p></td>
<td><p>Você precisará criar os certificados que são usados para federação de identidades com o Office 365. Para mais informações, consulte a seção “Certificados de servidor de federação” no tópico Plano e na implantação do AD FS para uso com login único em <a href="http://go.microsoft.com/fwlink/p/?linkid=285376">Lista de Verificação: Usar o AD FS para implementar e gerenciar o login único</a>.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Atribuir certificados para AD FS</p></td>
<td><p>Após criar os certificados que são utilizados para federação de identidades com o Office 365, você precisará instalá-los e atribuí-los.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Mover os usuários-piloto para Skype for Business Online</p></td>
<td><p>Após ter completado as etapas para preparar e configurar seu ambiente para Skype for Business Online, você poderá começar a mover usuários-piloto para o Lync Online.</p>
<p>Consulte <a href="lync-server-2013-move-users-to-lync-online.md">Mover usuários para Lync Online no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Administração de usuários em uma implantação híbrida</p></td>
<td><p>Para detalhes sobre como administrar usuários em uma implantação híbrida, consulte <a href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">Administrando usuários em uma implantação híbrida do Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>

