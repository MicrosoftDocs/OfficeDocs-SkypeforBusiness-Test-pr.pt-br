---
title: Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão
TOCTitle: Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão
ms:assetid: ba112df8-3bb4-48e4-a353-4bf9110ccd71
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412909(v=OCS.15)
ms:contentKeyID: 49307931
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma regra de conversão usando a compilação de uma ferramenta de regra de conversão

 

_**Tópico modificado em:** 2012-10-05_

Siga as etapas para definir a regra de conversão digitando um conjunto de valores na ferramenta **Criar uma Regra de Conversão** e possibilitando que o Painel de Controle do Lync Server gere o padrão de correspondência compatível e a regra de conversão. Se preferir, é possível gravar uma expressão regular manualmente para definir o padrão de correspondência e a regra de conversão. Para obter detalhes, consulte [Criar ou modificar uma regra de conversão manualmente](lync-server-2013-create-or-modify-a-translation-rule-manually.md).

## Para definir uma regra usando a ferramenta Compilar uma Regra de Conversão

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Para começar a definir uma regra de conversão, execute as etapas em [Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md) até a etapa 10 ou [Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md) até a etapa 9.

4.  Em **Nome** na página **Nova Regra de Conversão** ou **Editar Regra de Conversão**, digite um nome que descreve o padrão numérico que está convertido.

5.  (Opcional) Em **Descrição**, digite uma descrição da regra de conversão, por exemplo **Discagem de longa distância internacional EUA**.

6.  Na seção **Compilar uma Regra de Conversão** da caixa de diálogo, insira valores nos seguintes campos:
    
      - **Dígitos iniciais**: (Opcional) especifique os dígitos iniciais dos números com os quais você deseja que o padrão corresponda. Por exemplo, digite **+** nesse campo para corresponder os números no formato E.164 (que começa com +).
    
      - **Comprimento**: especifique o número de dígitos no padrão de correspondência e selecione se deseja que o padrão corresponda a números exatamente com esse comprimento, com um comprimento menor ou qualquer comprimento. Por exemplo, digite **11** e selecione **No mínimo** na lista suspensa para fazer a correspondência de números com no mínimo 11 dígitos de comprimento.
    
      - **Dígitos a serem removidos**: (Opcional) especifique o número de dígitos iniciais a serem removidos. Por exemplo, digite **1** para retirar o **+** do início do número.
    
      - **Dígitos a adicionar**: (Opcional) especifique os dígitos a serem anexados aos números convertidos. Por exemplo, digite **011** se quiser que 011 seja anexado aos números convertidos quando a regra é aplicada.
    
    Os valores inseridos nesses campos são refletidos nos campos **Padrão a ser correspondido** e **Regra de conversão**. Por exemplo, se você especificar os valores do exemplo anterior, a expressão regular resultante no campo **Padrão a ser correspondido** será:
    
    **^\\+(\\d{9}\\d+)$**
    
    O campo **Regra de conversão** especifica um padrão para o formato de números convertidos. Esse padrão tem duas partes:
    
      - Um valor (por exemplo, **$1**) que representa o número de dígitos no padrão correspondido
    
      - (Opcional) Um valor que pode ser anexado digitando no campo **Dígitos a adicionar**
    
    Usando os valores do exemplo anterior, **011$1** aparece no campo **Regra de conversão**.
    
    Quando essa regra de conversão é aplicada, +441235551010 se torna 011441235551010.

7.  Clique em **OK** para salvar a regra de tradução.

8.  Clique em **OK** para salvar a configuração de tronco.

9.  Na página **Configuração do Tronco**, clique em **Confirmar** e clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que criar ou modificar uma regra de tradução, será necessário executar o comando <strong>Confirmar tudo</strong> para publicar a alteração de configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação Operações.

## Consulte Também

#### Tarefas

[Criar ou modificar uma regra de conversão manualmente](lync-server-2013-create-or-modify-a-translation-rule-manually.md)  
[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Conceitos

[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)

