---
title: 'Lync Server 2013: Pré-requisitos do plug-in Lync VDI'
TOCTitle: Pré-requisitos do plug-in Lync VDI
ms:assetid: da25a976-7624-4dfc-b332-9c4db4ee78da
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205304(v=OCS.15)
ms:contentKeyID: 49308292
ms.date: 03/08/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos do plug-in Lync VDI no Lync Server 2013

 

_**Tópico modificado em:** 2017-03-07_

Em um ambiente de infraestrutura de desktop virtual (VDI), as máquinas virtuais e o computador local do usuário devem atender os requisitos destacados nesta seção.

> [!NOTE]  
> Consulte o provedor de solução de virtualização para obter detalhes sobre como instalar e implantar o ambiente virtualizado. Para obter informações sobre como implantar um ambiente virtualizado com base nos Serviços de Área de Trabalho Remota e Hyper-V, consulte os artigos a seguir na Biblioteca TechNet da Microsoft:<ul>
> 
> <li><p>Hyper-V em <a href="http://go.microsoft.com/fwlink/p/?linkid=247514" class="uri">http://go.microsoft.com/fwlink/p/?linkid=247514</a></p></li>
> 
> 
> <li><p>Serviços de Área de Trabalho Remota do Windows Server 2008 R2 em <a href="http://go.microsoft.com/fwlink/p/?linkid=247513" class="uri">http://go.microsoft.com/fwlink/p/?linkid=247513</a></p></li></ul>


A seguir estão requisitos para máquinas virtuais executando no computador do centro de dados:

  - Máquinas virtuais devem ser configuradas com o Windows 8, Windows 7 ou Windows Server 2008 R2 com os service packs mais recentes.

A seguir estão requisitos para o usuário e seu computador local:

  - O usuário precisa estar hospedado em Lync Server 2013.

  - O computador local deve estar executando o Windows Embedded Standard 7 com SP1, Windows 7 com SP1 ou Windows 8.

  - Se você estiver usando os Serviços de Área de Trabalho Remota, o plug-in VDI do Lync bitness (isto é, sempre que o aplicativo tiver 32 bits ou 64 bits) deve corresponder o bitness do sistema operacional do computador local. O bitness do sistema operacional no computador local e o sistema operacional na máquina virtual não precisam corresponder. Se você estiver usando outra solução de virtualização ou plataforma, consulte o guia do seu provedor de solução de virtualização sobre os requisitos de bitness.

  - O computador local deve estar executando a versão mais atual do cliente de área de trabalho remota. Instale as últimas atualizações do cliente dos Serviços da Área de Trabalho Remota da Microsoft ou o software do cliente de área de trabalho remota mais atual do seu provedor de solução de virtualização. Para obter as últimas atualizações dos Serviços de Área de Trabalho Remota, consulte [http://go.microsoft.com/fwlink/p/?LinkId=268032](http://go.microsoft.com/fwlink/p/?linkid=268032).

  - No computador local, as configurações do cliente de área de trabalho remota devem ser definidas para que o áudio reproduza o computador local e para que a gravação remota esteja desabilitada. Para definir estas configurações para a Conexão de Área de Trabalho Remota no Windows, consulte a próxima seção, “Para definir as configurações de Conexão da Área de Trabalho Remota”.

## Para definir as configurações da Conexão da Área de Trabalho Remota

Para preparar a Conexão da Área de Trabalho Remota no Windows para o plug-in VDI do Lync, siga estas etapas.

1.  Se o computador local está executando o Windows 8, pule esta etapa. Se o computador local estiver executando o Windows 7 com SP1, instale a versão mais atual do Windows 8 do cliente dos Serviços de Área de Trabalho Remota, disponível em [http://go.microsoft.com/fwlink/p/?LinkId=268032](http://go.microsoft.com/fwlink/p/?linkid=268032).

2.  Inicie o cliente dos Serviços de Área de Trabalho Remota clicando em **Iniciar** e em **Conexão da Área de Trabalho Remota** .

3.  Clique em **Opções** .

4.  Clique na guia **Recursos locais** . Em **Áudio remoto** , clique em **Configurações** e faça o seguinte:
    
      - Em **Reprodução de áudio remoto** , selecione **Reproduzir neste computador** .
    
      - Em **Gravação de áudio remoto** , selecione **Não gravar** .
    
      - Clique em **OK** .

5.  Clique na guia **Experiência** . Em **Desempenho** , desmarque a caixa de seleção **Cache de bitmap persistente** .

6.  Clique na guia **Geral** . Em **Computador** , digite o nome da máquina virtual e clique em **Conectar** .

