---
title: 'Lync Server 2013: Exportar sua topologia e copiá-la na mídia externa para instalação de borda'
TOCTitle: Exportar sua topologia e copiá-la na mídia externa para instalação de borda
ms:assetid: def9f416-c519-4a72-b242-7d3057d9c1fd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398983(v=OCS.15)
ms:contentKeyID: 49308353
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda

 

_**Tópico modificado em:** 2012-09-08_

Após publicar a topologia, o Assistente de Implantação do Lync Server precisará acessar os dados do Repositório de Gerenciamento Central para iniciar o processo de implantação no servidor. Na rede interna, os dados podem ser acessados diretamente dos servidores, mas os Servidores de Borda que não estão no domínio interno não podem acessar esses dados. Para tornar os dados de configuração da topologia disponíveis para uma implantação de Servidor de Borda, você terá que exportar os dados da topologia para um arquivo e copiá-los na mídia externa (por exemplo, uma unidade USB ou um compartilhamento de rede que possa ser acessado do Servidor de Borda) antes de executar o Assistente de Implantação do Lync Server no Servidor de Borda. Use o seguinte procedimento para tornar os dados de configuração da topologia disponíveis no Servidor de Borda que você está implantando.

> [!NOTE]  
> Após a instalação do Lync Server 2013 em um Servidor de Borda, gerencie o Servidor de Borda usando as ferramentas administrativas na rede interna, que replica automaticamente a configuração para quaisquer Servidores de Borda em sua implantação. A única exceção é a atribuição e instalação de certificados, além do início e término de serviços, que precisa ser feita no Servidor de Borda.

## Para disponibilizar os dados de sua topologia em um Servidor de Borda usando o Shell de Gerenciamento do Lync Server

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  No Shell de Gerenciamento do Lync Server, execute o seguinte cmdlet:
    
        Export-CsConfiguration -FileName <ConfigurationFilePath.zip>

3.  Copie o arquivo exportado para a mídia externa (por exemplo, uma unidade USB ou um compartilhamento de rede que seja acessível no Servidor de Borda durante a implantação).

