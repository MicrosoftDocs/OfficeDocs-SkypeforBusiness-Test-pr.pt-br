---
title: Criar ou modificar uma regra de conversão manualmente
TOCTitle: Criar ou modificar uma regra de conversão manualmente
ms:assetid: 049d1db3-af58-48c5-be89-52e1d068a4bd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398099(v=OCS.15)
ms:contentKeyID: 49305726
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma regra de conversão manualmente

 

_**Tópico modificado em:** 2012-08-06_

Siga estas etapas para definir uma regra de conversão desenvolvendo uma expressão regular para o padrão de correspondência e a regra de conversão. Se preferir, você pode inserir um conjunto de valores na ferramenta **Criar uma Regra de Conversão** e permitir que o Painel de Controle do Lync Server gere o padrão de correspondência adequado e a regra de conversão para você. Para obter detalhes, consulte [Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md).

## Como definir uma regra de conversão manualmente

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Para começar a definir uma regra de conversão, siga as etapas de [Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md) até a etapa 10 ou de [Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md) até a etapa 9.

4.  No campo **Nome**, na página **Nova Regra de Conversão** ou **Editar Regra de Conversão**, digite um nome que descreva o padrão de número sendo convertido.

5.  (Opcional) No campo **Descrição**, digite a descrição da regra de conversção, por exemplo **Discagem internacional de longa distância dos EUA**.

6.  Clique em **Editar** na parte inferior da seção **Criar uma Regra de Conversão**.

7.  Insira no campo**Digite uma Expressão Regular** o seguinte:
    
      - No campo **Corresponder a este padrão**, especifique o padrão que será usado para corresponder os números a serem convertidos.
    
      - No campo **Regra de conversão**, especifique o padrão para o formato dos números convertidos.
    
    Por exemple, se você inserir **^\\+(\\d{9}\\d+)$** no campo **Corresponder a este padrão** e **011$1** no campo **Regra de conversão**, a regra converterá +441235551010 em 011441235551010.

8.  Clique em **OK** para salvar a regra de conversão.

9.  Clique em **OK** para salvar a configuração do tronco.

10. Na página **Configuração do Tronco**, clique em **Confirmar** e, depois, em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que você criar ou modificar uma regra de conversão, você deve executar o comando <strong>Confirmar tudo</strong> para publicar a mudança na configuração. Para obter mais detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

## Consulte Também

#### Tarefas

[Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)  
[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Conceitos

[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)

