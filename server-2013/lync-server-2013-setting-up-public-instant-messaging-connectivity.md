---
title: 'Lync Server 2013: Configurar conectividade de mensagens instantâneas públicas'
TOCTitle: Configurar conectividade de mensagens instantâneas públicas
ms:assetid: 816dea2a-96fa-4a36-b6c2-a9402675868b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205041(v=OCS.15)
ms:contentKeyID: 49307287
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar conectividade de mensagens instantâneas públicas no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Se sua organização desejar oferecer suporte à conectividade pública de mensagens instantâneas com o AOL, você não pode usar o Assistente de Implantação do Lync Server para solicitar o certificado. Em vez disso, siga o procedimento abaixo.

## Configurando a conectividade para redes públicas de mensagens instantâneas

1.  Em um servidor front-end, abra o Construtor de Topologias. Expanda os pools de borda e clique com o botão direito do mouse no servidor de borda ou pool de servidores de borda. Selecione Editar propriedades.

2.  Em Editar propriedades, em Geral, selecione Habilitar federação para esse pool de borda (porta 5061). Clique em OK.

3.  Clique em Ação, selecione Topologia e, depois, Publicar. Quando for consultado sobre a publicação da topologia, clique em Avançar. Quando a publicação estiver concluída, clique em Concluir.

4.  No servidor de borda, abra o assistente Implantação do Lync Server. Clique em Instalar ou Atualizar Sistema do Lync Server e, então, clique em Instalar ou Remover Componentes do Lync Server. Clique em Executar Novamente.

5.  Em Instalar Componentes do Lync Server, clique em Avançar. A tela de resumo mostrará as ações conforme forem executadas. Depois que a implantação estiver concluída, clique em Exibir Log para exibir os arquivos de log disponíveis. Clique em Concluir para concluir a implantação.

## Para criar uma solicitação de certificado para a interface externa do Servidor de Borda para oferecer suporte à conectividade pública de IM com o AOL

1.  Quando o modelo necessário estiver disponível para a autoridade de certificação, use o seguinte cmdlet Windows PowerShell no Servidor de Borda para solicitar o certificado:
    
        Request-CsCertificate -New -Type AccessEdgeExternal  -Output C:\ <certfilename.txt or certfilename.csr>  -ClientEku $true -Template <template name>
    
    O nome do certificado padrão do modelo usado em Lync Server é Servidor Web. Somente especifique o \<nome do modelo\> quando precisar usar um modelo diferente do padrão.
    
    > [!IMPORTANT]  
    > Se sua organização desejar oferecer suporte à conectividade a redes públicas de IM com o AOL, você deverá usar o Windows PowerShell em vez do Assistente de Certificados para solicitar o certificado a ser atribuído à borda externa do serviço de Borda de Acesso. Isso ocorre porque o modelo de Servidor Web da Autoridade (CA) usado pelo Assistente de Certificados para solicitar um certificado não oferece suporte à configuração de cliente EKU. Antes de usar o Windows PowerShell para criar o certificado, o administrador deverá criar e implantar um novo modelo que oferece suporte ao cliente EKU.
