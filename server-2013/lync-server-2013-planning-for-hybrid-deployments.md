---
title: 'Lync Server 2013: Planning for hybrid Lync Server deployments'
TOCTitle: Planning for hybrid Lync Server deployments
ms:assetid: f8b3d240-bc2e-42c9-acf8-d532d641a14c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205403(v=OCS.15)
ms:contentKeyID: 49308660
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de implantações híbridas do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Você deve considerar os seguintes requisitos para usuários e infraestrutura de rede ao se planejar para uma implantação híbrida.

## Requisitos de infraestrutura

Você deve ter o seguinte disponível em seu ambiente para implementar e configurar uma implantação híbrida do Lync Server 2013.

  - Um locatário do Office 365 com Lync Online habilitado.

  - Um Servidor AD FS (Serviços de Federação do Active Directory) local ou que usa o Microsoft Azure. Para obter mais informações sobre o AD FS, consulte [Serviços de Federação de Diretório Ativo (AD FS) 2.0](http://go.microsoft.com/fwlink/p/?linkid=393795) ou [Configurar os Serviços de Federação do Active Directory para o Pacote do Windows Azure](http://go.microsoft.com/fwlink/p/?linkid=522475).

  - Em uma implantação local do Lync Server 2013 ou Lync Server 2010 com Atualizações Cumulativas para o Lync Server 2010: aplicadas em março de 2013 ou posterior.

  - Ferramentas administrativas do Lync Server 2013.

  - Sincronização de Diretório. Para obter detalhes sobre Sincronização de Diretório, consulte [Gerenciamento Híbrido de Identidade](http://go.microsoft.com/fwlink/p/?linkid=231010).

## Suporte ao cliente Lync

Existem algumas diferenças entre os recursos com suporte nos clientes do Lync, bem como os recursos disponíveis nos ambientes local e online. Antes de decidir onde deseja hospedar os usuários de sua organização, você pode exibir o suporte ao cliente das várias configurações do Lync Server. Os seguintes clientes são suportados com o Skype for Business Online em uma implantação híbrida do Lync:

  - Lync 2010

  - Lync 2013

  - Aplicativo Lync Windows Store

  - Lync Web App

  - Lync Mobile

  - Lync para Mac 2011

  - Sistema de Salas do Lync

  - Lync Basic 2013

Para detalhes sobre suporte ao cliente, consulte os seguintes tópicos:

  - [Clientes do Lync Online](http://go.microsoft.com/fwlink/?linkid=281902)

  - [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md)

  - [Tabela de comparação de clientes móveis para o Lync Server 2013](lync-server-2013-mobile-client-comparison-tables.md)

## Requisitos de topologia

Para configurar sua implantação do Lync Server 2013 como híbrida com o Skype for Business Online, você deve ter uma das seguintes topologias com suporte:

  - Microsoft Office Communications Server 2007 R2 com Lync Server 2013 local. A federação da Lync Server 2013 do Servidor de Borda e o próximo servidor de salto da Servidor de Borda de federação devem executar o Lync Server 2013 e deve haver um Repositório de Gerenciamento Central. A Servidor de Borda e o pool devem ser implantados localmente.
    
    > [!IMPORTANT]  
    > Apesar de esta topologia ser suportada, algumas funcionalidades podem ser limitadas. Por exemplo, informações de presença entre usuários do Microsoft Lync Online e usuários do local do Office Communications Server 2007 R2 podem não funcionar como o esperado.

  - Microsoft Lync Server 2010 com Atualizações Cumulativas para o Lync Server 2010: aplicadas em março de 2013 (ou atualização posterior) e as ferramentas administrativas locais do Lync Server 2013 instaladas. O Servidor de Borda de federação e o servidor do próximo salto do Servidor de Borda de federação devem estar executando o Microsoft Lync Server 2010, com as atualizações cumulativas de março de 2013 (ou posterior) aplicadas, ou o Lync Server 2013.
    
    > [!IMPORTANT]  
    > .As ferramentas administrativas do Lync Server 2013 devem ser instaladas em um servidor distinto que tenha acesso para se conectar à implementação do Lync Server 2010 existente. O cmdlet Move-CsUser para mover usuários de sua implementação local para o Lync Online deve ser executado a partir das ferramentas administrativas do Lync Server 2013 conectadas a sua implementação no local.

  - Uma implantação do Lync Server 2013 com todos os servidores executando o Lync Server 2013.

Para obter mais informações sobre as topologias suportadas, consulte Topologias de referência do [Topologias suportadas no Lync Server 2013](lync-server-2013-supported-topologies.md), e do Lync Server 2013 [para Implantações híbridas da empresa](http://go.microsoft.com/fwlink/p/?linkid=398709).

Para obter informações de solução de problemas sobre implantações híbridas e conexão do PowerShell com o Lync Online, consulte [Lync Online: Lync PowerShell e soluções de problemas híbridos](http://go.microsoft.com/fwlink/p/?linkid=306718).

## Requisitos das listas de permissões/bloqueios da federação

A lista Domínios permitidos contém domínios com UM FQDN (nome de domínio totalmente qualificado) de borda parceiro configurado. Por vezes, eles são chamados de *servidores parceiros permitidos* ou *parceiros de federação direto* . Você deve estar familiarizado com a diferença entre a federação aberta e a federação fechada, conhecidas respectivamente como *descoberta de parceiros* e *lista de domínios dos parceiros permitidos* nas implantações locais.

Os seguintes requisitos devem ser atendidos para configurar com êxito uma implantação híbrida:

  - O domínio correspondente deve ser o mesmo configurado para sua implantação local e seu locatário do Office 365. Se a descoberta de parceiros estiver habilitada na implantação local, a federação aberta deverá ser configurada para seu locatário online. Caso contrário, a federação fechada deverá ser configurada para seu locatário online.

  - A lista de domínios bloqueados da implantação local deve corresponder exatamente à do seu locatário online.

  - A lista de domínios permitidos da implantação local deve corresponder exatamente à do seu locatário online.

  - A federação deve ser habilitada para as comunicações externas com o locatário online, cuja configuração é feita com o Painel de Controle do Lync Online.

## Configurações de DNS

Quando você cria registros SRV DNS para implantações híbridas, os registros, \_sipfederationtls.\_tcp.\<domain\> e \_sip.\_tls.\<domain\> devem indicar o Proxy de Acesso local.

## Considerações sobre o firewall

Os computadores de sua rede devem ser capazes de realizar pesquisas DNS padrão na Internet. Se esses computadores puderem acessar os sites padrão da Internet, sua rede atenderá a esse requisito.

Dependendo do local de seu data center do Microsoft Online Services, você também deverá configurar seus dispositivos de rede do firewall para que aceitem conexões baseadas em nomes de domínio com coringa (por exemplo, todo o tráfego de \*.outlook.com). Se os firewalls de sua organização não oferecem suporte às configurações de nome com coringa, você deve determinar manualmente o intervalo de endereço IP que deseja permitir e as portas especificadas.

Consulte o tópico da ajuda [URLs do Office 365 e intervalos de endereços IP](http://go.microsoft.com/fwlink/p/?linkid=252942).

## Requisitos de porta e protocolo

Além dos requisitos de porta para a comunicação interna do Lync Server 2013, você também deve configurar as portas a seguir.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo/porta</th>
<th>Aplicativos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP 443</p></td>
<td><p>Entrada aberta</p><ul><li><p>Serviços de Federação do Active Directory (função de servidor de federação)</p>
<p>Para obter mais informações, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=281899">Noções básicas dos serviços de função do AD FS</a>.</p></li><li><p>Serviços de Federação do Active Directory (função de servidor proxy)</p></li><li><p>Portal do Microsoft Online Services</p></li><li><p>Portal da Minha Empresa</p></li><li><p>Outlook Web App</p></li><li><p>Cliente Lync (comunicação para o Lync Online a partir do Lync Server local)</p></li></ul></td>
</tr>
<tr class="even">
<td><p>TCP 80 e 443</p></td>
<td><p>Entrada aberta</p><ul><li><p>Ferramenta de Sincronização de Diretório do Microsoft Online Services</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>TCP 5061</p></td>
<td><p>Entrada/saída abertas no Servidor de Borda</p></td>
</tr>
<tr class="even">
<td><p>PSOM/TLS 443</p></td>
<td><p>Entrada/saída abertas para sessões de compartilhamento de dados</p></td>
</tr>
<tr class="odd">
<td><p>STUN/TCP 443</p></td>
<td><p>Entrada/saída abertas para sessões de áudio, vídeo e compartilhamento de aplicativos</p></td>
</tr>
<tr class="even">
<td><p>STUN/UDP 3478</p></td>
<td><p>Entrada/saída abertas para sessões de áudio e vídeo</p></td>
</tr>
<tr class="odd">
<td><p>RTP/TCP 50000-59999</p></td>
<td><p>Saída aberta para sessões de áudio e vídeo</p></td>
</tr>
<tr class="even">
<td><p>TCP 443</p></td>
<td><p>Entrada aberta</p><ul><li><p>Serviços de Federação do Active Directory (função de servidor de federação)</p>
<p>Para obter mais informações, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=281899">Noções básicas dos serviços de função do AD FS</a>.</p></li><li><p>Serviços de Federação do Active Directory (função de servidor proxy)</p></li><li><p>Portal do Microsoft Online Services</p></li><li><p>Portal da Minha Empresa</p></li><li><p>Outlook Web App</p></li><li><p>Cliente Lync (comunicação para o Lync Online a partir do Lync Server local)</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>TCP 80 e 443</p></td>
<td><p>Entrada aberta</p><ul><li><p>Ferramenta de Sincronização de Diretório do Microsoft Online Services</p></li></ul></td>
</tr>
<tr class="even">
<td><p>TCP 5061</p></td>
<td><p>Entrada/saída abertas no Servidor de Borda</p></td>
</tr>
<tr class="odd">
<td><p>PSOM/TLS 443</p></td>
<td><p>Entrada/saída abertas para sessões de compartilhamento de dados</p></td>
</tr>
<tr class="even">
<td><p>STUN/TCP 443</p></td>
<td><p>Entrada/saída abertas para sessões de áudio, vídeo e compartilhamento de aplicativos</p></td>
</tr>
<tr class="odd">
<td><p>STUN/UDP 3478</p></td>
<td><p>Entrada/saída abertas para sessões de áudio e vídeo</p></td>
</tr>
<tr class="even">
<td><p>RTP/TCP 50000-59999</p></td>
<td><p>Saída aberta para sessões de áudio e vídeo</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Se precisar fazer a federação com parceiros que executam o Office Communications Server 2007, você deverá abrir as portas RTP/UDP e RTP/TCP de entrada/saída 50000-59999. Para obter mais informações sobre os requisitos de áudio/vídeo do firewall, consulte <a href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Determinar firewall A/V externo e requisitos de porta para Lync Server 2013</a>. Para obter mais informações sobre portas e protocolos, consulte <a href="lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md">Resumo de porta - borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013</a>.

## Dados e contas do usuário

Em uma implantação híbrida do Lync Server 2013, qualquer usuário que você quiser hospedar no Lync Online deverá ser primeiro criado na implantação local para que a conta de usuário seja criada no Serviços de Domínio Active Directory. Em seguida, você pode mover o usuário para o Skype for Business Online, o que não moverá a lista de contatos do usuário.

Se você sincronizar todas as contas de usuários entre as implantações do Lync on-premises e do Lync Online com AD FS e Dirsync, terá de sincronizar as contas do AD para todos os usuários do Lync em sua organização entre as implantações do Lync local e online, mesmo se os usuários não forem movidos para o Lync Online. Se você não sincronizar todos os usuários, a comunicação entre os usuários online e locais em sua organização pode não funcionar como o esperado.

> [!IMPORTANT]  
> Se o usuário for criado com o portal online do Office 365, a conta de usuário não será sincronizada com o Active Directory local nem o usuário existirá nele. Se você já tiver criado usuários no Lync Online, e desejar configurar o híbridos com o Lync Server local, consulte <a href="lync-server-2013-moving-users-from-lync-online-to-lync-on-premises.md">Mover usuários do Lync Online para o Lync no local no Lync Server 2013</a>.

Você também deve considerar os seguintes problemas relacionados ao usuário ao se planejar para uma implantação híbrida.

  - **Contatos do usuário**   O limite de contatos para usuários do Lync Online é 250. Todos os contatos além deste número serão removidos da lista de contatos do usuário quando a conta for movida para o Lync Online.

  - **Sistema de mensagens instantâneas e presença**   As listas de contatos, os grupos e as ACLs (lista de controle de acesso) do usuário são migrados com a conta de usuário.

  - **Dados de conferências, conteúdos de reuniões e reuniões agendadas**   Este conteúdo não é migrado com a conta de usuário. Os usuários devem reagendar as reuniões depois que as contas são migradas para o Lync Online.

## Recursos e políticas do usuário

  - Em uma implantação híbrida do Lync Server 2013, os usuários podem estar habilitados para o sistema de mensagens instantâneas, voz e reuniões, seja localmente ou online, porém não para todos simultaneamente.

  - **Cliente Lync**    Alguns usuários podem exigir uma nova versão de cliente quando são movidos para o Lync Online. Para o Office Communications Server 2007 R2, os usuários devem ser movidos para um pool do Lync Server 2013 antes da migração para o Lync Online.
    
    Para obter mais informações sobre o suporte ao cliente, consulte [Clientes do Lync Online](http://go.microsoft.com/fwlink/p/?linkid=281902) e [Clientes do Lync e configurações de porta de rede](http://go.microsoft.com/fwlink/p/?linkid=281901) .

  - **Configuração e políticas locais (não-usuário)**   As políticas online e local exigem uma configuração separada. Você não pode definir políticas globais que se aplicam a ambos.

