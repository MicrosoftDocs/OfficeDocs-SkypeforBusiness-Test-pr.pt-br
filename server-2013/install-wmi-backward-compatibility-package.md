---
title: Instalar o pacote de Compatibilidade com Versões Anteriores
TOCTitle: Instalar o pacote de Compatibilidade com Versões Anteriores
ms:assetid: 38797fbd-06a0-4008-b099-158e7b5d7703
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204816(v=OCS.15)
ms:contentKeyID: 49306393
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar o pacote de Compatibilidade com Versões Anteriores

 

_**Tópico modificado em:** 2012-10-02_

Se você tentar executar o assistente de Fusão do Construtor de Topologias sem instalar o pacote de Compatibilidade com Versões Anteriores da WMI, você verá o seguinte erro:

![Mensagem de erro WMI](images/JJ204816.a007d2f2-fc85-430c-91eb-382b032469af(OCS.15).jpg "Mensagem de erro WMI")

Se tentar executar o cmdlet **Merge-CsLegacytopology** sem instalar o pacote de Compatibilidade com Versões Anteriores da WMI, você verá o seguinte erro:

![Erro do Provedor WMI do Windows PowerShell](images/JJ204816.c510824e-1807-4c7e-bb28-c6cfea2eac1d(OCS.15).jpg "Erro do Provedor WMI do Windows PowerShell")

Para instalar o pacote de Compatibilidade com Versões Anteriores da WMI

1.  Em sua mídia de instalação, navegue para \\SETUP\\AMD64\\SETUP\\OCSWMIBC.MSI.

2.  Instale o OCSWMIBC.MSI.
    
    > [!IMPORTANT]  
    > O OCSWMIBC.msi deve ser instalado no computador em que o assistente de Fusão do Construtor de Topologias será executado. No entanto, é recomendável instalar o OCSWMIBC.msi em todos os servidores front-end de sua topologia.    
    > [!IMPORTANT]  
    > O OCSWMIBC.msi pode ser instalado em qualquer computador do domínio que tenha acesso aos componentes principais do Lync Server 2013 e o shell de gerenciamento do Lync Server 2013 e também acesso à topologia do Office Communications Server 2007 R2 (provedor da WMI para AD DS (Serviços de Domínio Active Directory ) e SQL Server).
