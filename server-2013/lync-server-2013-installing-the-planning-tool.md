---
title: 'Lync Server 2013: Instalando a Ferramenta de Planejamento'
TOCTitle: Instalando a Ferramenta de Planejamento
ms:assetid: ebdc9e26-4b22-4b02-85b9-7462bcfe7c93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615046(v=OCS.15)
ms:contentKeyID: 52057748
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando a Ferramenta de Planejamento no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

Antes de começar a criação e o planejamento da infraestrutura do Lync Server 2013 usando a Microsoft Lync Server 2013, Ferramenta de Planejamento, primeiro instale a Ferramenta de Planejamento. Não é necessário implantar a Ferramenta de Planejamento em uma estação de trabalho ou servidor que faça parte do domínio ou da infraestrutura na qual pretende instalar o Lync Server 2013. O arquivo Leiame que acompanha a Ferramenta de Planejamento apresenta informações detalhadas importantes sobre a instalação e o uso da ferramenta. Algumas das informações no arquivo Leiame estão reproduzidas aqui para esclarecimento.

> [!IMPORTANT]  
> O Ferramenta de Planejamento exige a instalação por um usuário com direitos e permissões de administrador no computador no qual a ferramenta será instalada.

Os sistemas operacionais suportados para instalação e operação do Ferramenta de Planejamento são:

  - Windows 8

  - Windows 8.1

  - Windows Server 2012

  - Windows Server 2012 R2

  - Windows 7, edição de 32 bits

  - Windows 7, edição de 64 bits usando Windows no Win32 (WOW)

  - Windows Server 2008 R2, usando WOW

Além disso, o Ferramenta de Planejamento exige o Microsoft.NET Framework 4.5.

Depois que os requisitos de pré-instalação forem atendidos, você poderá instalar o Ferramenta de Planejamento.

## Para instalar a Ferramenta de Planejamento

1.  Faça logon no computador local como membro do grupo Administradores.

2.  Usando o Windows Explorer ou uma janela de comando, localize o diretório onde baixou os arquivos de instalação do Ferramenta de Planejamento.

3.  Localize o LyncPlanningTool.msi. No Windows Explorer, clique duas vezes no arquivo. Na janela de comando, digite o nome do arquivo e pressione **Enter** para executá-lo.

4.  Na página de Boas-vindas do **Microsoft Lync Server 2013, Assistente de instalação da ferramenta de planejamento** , clique em **Avançar** .

5.  Revise o **Contrato de Licença de Usuário Final** , selecione **Aceito os termos do Contrato de Licença** se você escolher aceitar os termos de uso do contrato de licença e clique em **Avançar** .

6.  Escolha onde instalar os arquivos da ferramenta de planejamento. O local padrão é C:\\Arquivos de Programas (x86)\\Microsoft Lync Server 2013\\Ferramenta de planejamento. Se quiser alterar o local de instalação, clique em **Alterar** . Em **Alterar pasta de destino** , procure ou digite o local para instalar os arquivos, clique em **OK** e, depois, em **Avançar** .

7.  Agora, o instalador está pronto para instalar o Ferramenta de Planejamento. Clique em **Instalar** para começar o processo de instalação.

8.  A instalação será iniciada e o andamento será exibido. Após a conclusão da instalação, clique em **Concluir** .

9.  O Ferramenta de Planejamento está pronto para uso.

## Consulte Também

#### Conceitos

[Instalando software opcional no Lync Server 2013](lync-server-2013-installing-optional-software.md)

