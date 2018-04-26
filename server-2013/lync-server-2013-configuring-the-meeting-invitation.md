---
title: Configurando o convite de reunião no Lync Server 2013
TOCTitle: Configurando o convite de reunião no Lync Server 2013
ms:assetid: 7faa4797-0344-418b-9fa3-59dfb9c2baf7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398638(v=OCS.15)
ms:contentKeyID: 49307260
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o convite de reunião no Lync Server 2013

 

_**Tópico modificado em:** 2013-07-16_

Você pode personalizar convites para reuniões enviados por Suplemento de Reunião Online para Lync 2013 incluindo os itens opcionais a seguir no corpo do convite da reunião:

  - **O logotipo da sua empresa** Adicione o logotipo da sua empresa aos convites de reunião usando a opção Logo URL. Se convites de reunião serão enviados a pessoas fora da empresa, a imagem deve estar localizada em uma URL pública. Os formatos de imagem suportados são GIF e JPG. Embora Lync Server 2013 armazene a URL sem restrições de tamanho da imagem, para os melhores resultados, o tamanho máximo da imagem devem ser 30 pixels de altura por 188 pixels de largura.

  - **Ajuda Personalizada ou Link de Suporte** Adicione uma URL para ajuda da empresa ou website da equipe de suporte. Se os convites para reuniões serão enviados para pessoas fora da empresa, a URL deve estar disponível publicamente. O comprimento máximo da URL é 1 KB.

  - **Texto de isenção jurídica** Adicione uma URL para texto de isenção jurídica ou aviso que será exibido em todos os convites de reunião. Se os convites para reunião serão enviados a pessoas fora da empresa, a URL deve estar disponível publicamente. O comprimento máximo da URL é 1 KB.

  - **Texto de rodapé** Adicione o texto que será exibido como rodapé padrão no convite. O comprimento máximo do texto que pode ser adicionado é 2 KB.

Você pode configurar essas opções usando Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server.


**Para Personalizar o Convite para Reunião usando Painel de Controle do Lync Server**

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Configuração da reunião**.

4.  Na página **Configuração de reunião** , clique em **Novo** e siga um destes procedimentos:
    
      - Para criar uma política a nível local, clique em **Configuração local**. No campo de pesquisa **Selecionar um local**, digite todo ou parte do nome do local para o qual você deseja definir as configurações de participação de reunião. Na lista resultante de locais, clique no local desejado e em **OK**.
    
      - Para criar uma política a nível de pool, clique em **Configuração do pool**. No campo de pesquisa **Selecionar um serviço**, digite todo ou parte do nome do serviço do pool para o qual você deseja definir as configurações de participação de reunião. Na lista resultante de serviços, clique no pool desejado e em **OK**.

5.  Faça um dos seguintes:
    
      - No campo **URL do Logotipo**, digite a URL para a imagem de logotipo de sua empresa.
    
      - No campo **URL de ajuda**, digite a URL para o site de ajuda ou suporte de sua empresa.
    
      - No campo **Texto jurídico**, digite a URL para o texto jurídico ou de isenção que você deseja incluir nos convites para reunião.
    
      - No campo **Texto de rodapé**, digite o texto de rodapé, até 2 KB.

**Para Personalizar o Convite para Reunião usando Shell de Gerenciamento do Lync Server**

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsMeetingConfiguration** ou **Set-CsMeetingConfiguration** para criar ou configurar as opções de convite para reunião. Por exemplo, execute:
    
        New-CsMeetingConfiguration -Identity site:Redmond -EnableInviteCustomization $True -LogoURL "http://www.contoso.com/logo/contosobanner.gif" -HelpURL "http://www.contoso.com/support" -LegalURL "http://www.contoso.com/disclaimer" -CustomFooterText "Communications may be monitored or recorded."

