---
title: 'Lync Server 2013: Preparando o esquema do Active Directory'
TOCTitle: Preparando o esquema do Active Directory
ms:assetid: 067726ae-fd3f-4133-a32f-26d2603ac674
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398119(v=OCS.15)
ms:contentKeyID: 49305773
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando o esquema do Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Antes de começar a preparar o Serviços de Domínio Active Directory, você pode abrir os arquivos de esquema usando um editor de texto, como o Bloco de Notas do Windows, ou consultar [Extensões, classes e atributos do esquema do Active Directory usado pelo Lync Server 2013](lync-server-2013-active-directory-schema-extensions-classes-and-attributes-used-by-lync-server.md) para rever todas as extensões de esquema do Serviços de Domínio Active Directory que serão modificadas para o Lync Server 2013. O Lync Server utiliza quatro arquivos de esquema:

  - ExternalSchema.ldf, que é usado para a interoperabilidade com o Microsoft Exchange Server

  - ServerSchema.ldf, que é o arquivo de sistema do Lync Server 2013 principal

  - BackCompatSchema.ldf, que é usado para a interoperabilidade com quaisquer componentes de versões anteriores

  - VersionSchema.ldf, que é usado para informações sobre a versão do esquema preparado

Todos os arquivos .ldf são instalados durante a preparação do esquema, sem levar em conta se é uma migração de uma versão anterior ou se é uma instalação limpa. Esses arquivos de esquema são instalados na sequência mostrada na lista anterior e estão localizados na pasta \\Support\\schema na mídia de instalação.

As extensões de esquema do Lync Server são replicadas em todos os domínios, o que impacta no tráfego da rede. Execute a preparação do esquema quando a utilização da rede estiver baixa.

> [!NOTE]  
> Se você precisar adicionar suporte para Microsoft® Office Communicator Mobile 2007 R2 para Java e Microsoft® Office Communicator Mobile para os clientes de celulares Nokia 1.0 na implantação do Lync Server 2013, será necessário preparar o esquema do Active Directory para Microsoft Office Communications Server 2007 R2 durante a instalação do Lync Server 2013. Para obter as informações necessárias sobre software e documentação, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=207172">http://go.microsoft.com/fwlink/p/?linkId=207172</a>.

## Editor ADSI

Active Directory Service Interfaces Editor (Editor ADSI) é uma ferramenta de administração AD DS que você pode usar para verificar a preparação e a replicação de esquema.

O Editor ADSI é instalado por padrão quando você instala a função AD DS para transformar um servidor em um controlador de domínio. Para o Windows Server 2008 e o Windows Server 2008 R2, o Editor ADSI (adsiedit.msc) está incluído nas Ferramentas de Administração de Servidor Remoto (RSAT). Você também pode instalar o RSAT em servidores de membro de domínio ou servidores autônomos. O pacote RSAT é copiado a esses servidores por padrão quando o Windows é instalado, mas não é instalado por padrão. Instale as ferramentas individuais usando o Gerenciador de Servidores. O ADSI Edit está incluído em **Ferramentas de Administração de Funções** , **Ferramentas de Serviços de Domínio Active Directory** , **Ferramentas do Controlador de Domínio do Active Directory** .

Para o Windows Server 2003, o ADSI Edit está incluído nas Ferramentas de suporte. As Ferramentas de suporte estão disponíveis no CD do Windows Server 2003 na pasta \\SUPPORT\\TOOLS, ou você pode baixá-los em “Ferramentas de Suporte de 32 bits do Service Pack 2 do Windows Server 2003” em [http://go.microsoft.com/fwlink/p/?linkId=125770](http://go.microsoft.com/fwlink/p/?linkid=125770). Instruções para a instalação das Ferramentas de Suporte no CD do produto estão disponíveis em “Instalar Ferramentas de Suporte do Windows” em [http://go.microsoft.com/fwlink/p/?linkId=125771](http://go.microsoft.com/fwlink/p/?linkid=125771). O arquivo Adsiedit.dll é automaticamente registrado quando você instala as ferramentas de suporte. Se, no entanto, você tiver copiado os arquivos para o computador, deverá executar o comando **regsvr32** para registrar o arquivo adsiedit.dll e executar a ferramenta.

## Nesta seção

  - [Executando preparação de esquema de Active Directory no Lync Server 2013](lync-server-2013-running-schema-preparation.md)

  - [Verificando a replicação de esquema do Active Directory no Lync Server 2013](lync-server-2013-verifying-schema-replication.md)

## Consulte Também

#### Outros Recursos

[Preparando a floresta para Lync Server 2013](lync-server-2013-preparing-the-forest.md)  
[Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md)

