---
title: Configurando o modo de exibição de galeria
TOCTitle: Configurando o modo de exibição de galeria
ms:assetid: 4a609178-47d8-4682-ac8d-29f882801924
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204871(v=OCS.15)
ms:contentKeyID: 49306626
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o modo de exibição de galeria

 

_**Tópico modificado em:** 2016-12-08_

No Lync Server 2013, você configura a conferência de vídeo no Modo de exibição de Galeria na política de conferência. O Modo de exibição de Galeria é ativado por padrão. Se você não deseja permitir o Modo de exibição de Galeria ou deseja permitir para alguns usuários apenas, você precisa desativar esse recurso na política de conferência.

Quando o vídeo de um participante da conferência não está disponível, a experiência do Modo de exibição de Galeria pode ser aprimorada se você implantar fotos de alta resolução, um novo recurso no Lync Server 2013. Fotos em alta resolução fornecem uma alternativa às fotos de contato em resolução limitada e menor, armazenadas em Serviços de Domínio Active Directory. As fotos em alta resolução são armazenadas na caixa de correio Exchange 2013 do usuário, e, portanto, requer que você integre o Lync Server 2013 ao Exchange 2013. Para detalhes, consulte o artigo do blog NextHop, "Integrando Exchange 2013 e Lync Server 2013," em [http://go.microsoft.com/fwlink/?linkid=260987\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=260987%26clcid=0x416).

> [!NOTE]  
> O conteúdo de cada blog e sua URL estão sujeitos a alterações sem aviso prévio.

Você pode visualizar ou modificar os parâmetros do Modo de exibição de Galeria utilizando o Painel de Controle do Lync Server 2013 ou um dos cmdlets a seguir:

  - **Get-CsConferencingPolicy**

  - **Set-CsConferencingPolicy**

  - **New-CsConferencingPolicy**

Configure o Modo de exibição de Galeria com uma das configurações de política de conferência a seguir:

  - **AllowMultiview**   Este parâmetro controla se um usuário pode organizar conferências de vídeo no Modo de exibição de Galeria. Este parâmetro se aplica a reuniões programadas e ad-hoc criadas pelo usuário.
    
    Exemplos:
    
      - Este parâmetro é definido como Verdadeiro para o Usuário A, que está hospedado em um pool Lync Server 2013. Reuniões organizadas pelo Usuário A permitem que os usuários participem e recebam diversos fluxos de vídeo.
    
      - Este parâmetro é definido como Falso para o Usuário B, que está hospedado em um pool Lync Server 2013. Reuniões organizadas pelo Usuário B possuem um único fluxo de vídeo que é similar à experiência de conferência de vídeo oferecida pelo Lync Server 2010.
    
    Este parâmetro determina quem pode organizar reuniões que permitem vários fluxos de vídeo. Os participantes nas reuniões que permitem vários fluxos de vídeo podem ou não ter permissão para receber vários fluxos de vídeo, com base nas permissões individuais (consulte a descrição para o parâmetro EnableMultiviewJoin).

  - **EnableMultiviewJoin**   Este parâmetro controla se um participante em uma reunião recebe a experiência de vídeo do Modo de exibição de Galeria em reuniões que o permitem. Este parâmetro controla a experiência do usuário em qualquer reunião o qual ele participe.
    
    Exemplos:
    
      - Este parâmetro é definido como Verdadeiro para o Usuário C. Este usuário pode receber diversos fluxos de vídeo ao participar de uma reunião organizada ou iniciada pelo Usuário A. O Usuário C recebe um único fluxo de vídeo que é similar à experiência de conferência de vídeo fornecida pelo Lync Server 2010 ao participar de uma reunião organizada ou iniciada pelo Usuário B.
    
      - Este parâmetro é definido como Falso para o Usuário D. Este usuário recebe um único fluxo de vídeo que é similar à experiência de conferência de vídeo fornecida pelo Lync Server 2010 ao participar de uma reunião organizada pelo Usuário A ou Usuário B.

O procedimento a seguir é um exemplo de uso do Shell de Gerenciamento do Lync Server para ativar a conferência de vídeo no Modo de exibição de Galeria.

## Para modificar a política de conferência para conferência de vídeo no Modo de exibição de Galeria

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Na linha de comando, execute o seguinte cmdlet para editar a política de conferência:
    
        Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -AllowMultiview $true -EnableMultiviewJoin $true

