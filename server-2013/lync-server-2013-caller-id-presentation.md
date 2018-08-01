---
title: 'Lync Server 2013: Apresentação de ID de Chamadas'
TOCTitle: Apresentação de ID de Chamadas
ms:assetid: 6a643961-a0a1-41d1-96ba-6c428a89d82e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204980(v=OCS.15)
ms:contentKeyID: 49306998
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Apresentação de ID de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Com o Lync Server 2010, o número de telefone da parte chamada (isto é, o número de telefone chamado) pode ser convertido do formato E.164 para o formato de discagem local exigido pelo *ponto de tronco* (isto é, o gateway associado, PBX ou tronco SIP). Para fazer isso, você deve definir uma ou mais regras de conversão para converter a URI de Solicitação antes de roteá-la para o ponto de tronco.

O Lync Server 2013 introduz a opção de também converter o número de telefone do chamador (ou seja, o número de telefone do qual o chamador está ligando) do formato E.164 para o formato de discagem local que é exigido pelo par de tronco. Por exemplo, é possível criar uma regra de conversão para remover o prefixo +44 do início de uma cadeia de caracteres de discagem e substituí-lo por 0144.

**Para configurar a ID de chamadas usando o Painel de Controle do Lync Server**

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Roteamento de Voz** e depois, em **Configuração do Tronco** .

4.  Na página **Configuração do Tronco** , clique duas vezes no tronco existente (por exemplo, o tronco **Global** ) para exibir a caixa de diálogo **Editar Configuração do Tronco** .

5.  Para configurar a apresentação da ID de chamadas:
    
      - Para escolher uma ou mais regras de uma lista de todas as regras de conversão disponíveis em sua implantação do Enterprise Voice, clique em **Selecionar** . Em **Regras de Conversão de Número de Chamada** , clique nas regras que você deseja associar ao tronco e clique em **OK** .
    
      - Para definir uma nova regra de conversão e associá-la ao tronco, clique em **Novo** . Para obter detalhes sobre a definição de uma nova regra, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação Implantação.
    
      - Para editar uma regra de conversão que já esteja associada ao tronco, clique no nome da regra e clique em **Exibir detalhes** . Para obter detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação de Implantação.
    
      - Para copiar uma regra de conversão existente para usar como ponto de partida para definir uma nova regra, clique no nome da regra e clique em **Copiar** e clique em **Copiar** . Para detalhes, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md).
    
      - Para remover uma regra de conversão do tronco, destaque o nome da regra e clique em **Remover** .
    

    > [!WARNING]  
    > Não associe regras de conversão a um tronco se não houver regras de conversão configuradas no ponto do tronco associado porque as duas regras podem entrar em conflito.


