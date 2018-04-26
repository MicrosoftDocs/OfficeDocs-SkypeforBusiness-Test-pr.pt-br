---
title: Habilitar bypass de mídia de rede
TOCTitle: Habilitar bypass de mídia de rede
ms:assetid: 95c4fa06-49d3-41ac-acdc-7dcda66e5508
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182552(v=OCS.15)
ms:contentKeyID: 49307514
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar bypass de mídia de rede

 

_**Tópico modificado em:** 2012-11-01_

Configurações de desvio de mídia aplicam-se globalmente por toda a implantação do Microsoft Lync Server 2013. O desvio de mídia permite que chamadas ignorem o Servidor de Mediação. Para detalhes sobre quando usar o desvio de mídia, consulte [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) na seção de Planejamento.

Você pode habilitar e configurar o desvio de mídia a partir do Painel de Controle do Lync Server.

## Para habilitar e configurar o desvio de mídia

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da Rede** e clique em **Global**.

4.  Na página **Global**, clique na configuração **Global**. Sempre existe somente uma configuração, sempre chamada Global.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Na página **Editar Configuração Global**, clique na opção **Habilitar desvio de mídia**.

7.  Selecione uma das seguintes opções:
    
      - **Sempre desviar**   Selecione esta opção para tentar o desvio de mídia em todas as chamadas. Esta opção estará indisponível se o controle de admissão de chamadas (CAC) estiver habilitado. Se o CAC não estiver habilitado, selecione esta opção nas seguintes situações:
        
          - Não existe a necessidade de controle de largura de banda.
        
          - Não existe a necessidade de uma configuração refinada para determinar quando o desvio deve acontecer.
        
          - Existe conectividade total entre gateways e clientes.
    
      - **Use a configuração de sites e região**   Se o CAC estiver habilitado, esta opção será selecionada por padrão e não poderá ser alterada. Quando esta opção está selecionada, a configuração de rede de sites e regiões será usada para determinar quando o desvio de mídia será possível. Se esta opção for selecionada, você pode optar por habilitar o desvio para sites que não estão mapeados. Clique na opção **Habilitar desvio para sites não mapeados** somente se você tiver um ou mais sites grandes associados à mesma região, que não possuem restrições de largura de banda (por exemplo, um site central grande) e se tiver também alguns sites de filial associados à mesma região que executa as restrições de largura de banda. Ao habilitar o desvio para sites não mapeados, a configuração é eficiente porque somente as sub-redes associadas aos sites de filial são especificadas, em vez da necessidade de especificas todas as sub-redes associadas as todos os sites. É recomendável não selecionar a opção **Habilitar desvio para sites não mapeados** se o CAC estiver habilitado.

8.  Clique em **Confirmar** para salvar suas alterações.

## Consulte Também

#### Tarefas

[Desabilitar bypass de mídia de rede](lync-server-2013-disabling-network-media-bypass.md)  

#### Conceitos

[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  

#### Outros Recursos

[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

