---
title: Criar perfis da política de largura de banda no Lync Server 2013
TOCTitle: Criar perfis da política de largura de banda no Lync Server 2013
ms:assetid: a71881ef-b04a-465e-9abb-0577bfd182f3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412785(v=OCS.15)
ms:contentKeyID: 49307716
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar perfis da política de largura de banda no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

*Políticas de largura de banda* definem limitações de uso de largura de banda para modalidades de áudio e vídeo em tempo real. Elas são aplicadas a *perfis de política de largura de banda*, que podem ser aplicados a vários locais de rede para o controle de admissão de chamada.

Para orientações sobre quais limites de largura de banda devem ser definidos em sua implantação do CAC, consulte [Definindo seus requisitos de controle de admissão de chamadas no Lync Server 2013](lync-server-2013-defining-your-requirements-for-call-admission-control.md) na documentação de Planejamento.

Para detalhes sobre como trabalhar com políticas de largura de banda e perfis de política, consulte a documentação Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - [New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkBandwidthPolicyProfile)

  - [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

  - [Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkBandwidthPolicyProfile)

  - [Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)

As políticas de exemplo criadas no procedimento a seguir definem limites para o tráfego de áudio geral, sessões de áudio individuais, tráfego de vídeo geral e sessões de vídeo individuais. Por exemplo, o perfil de política de largura de banda 5Mb\_Link define os seguintes limites:

  - Limite de Áudio: 2.000 kbps

  - Limite de Sessão de Áudio: 200 kbps

  - Limite de Vídeo: 1.400 kbps

  - Limite de Sessão de Vídeo: 700 kbps

> [!NOTE]  
> O valor mínio para o Limite de Sessão de Áudio é 40 kbps. O valor mínimo para o Limite de Sessão de Vídeo é 100 kbps.

## Para criar perfis de política de largura de banda usando o Shell de Gerenciamento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para cada perfil de política de largura de banda que desejar criar, execute o cmdlet New-CsNetworkBandwidthPolicyProfile. Por exemplo, execute:
    
```
        New-CsNetworkBandwidthPolicyProfile -Identity 5Mb_Link -Description "BW profile for 5Mb links" -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400  -VideoBWSessionLimit 700
```
```    
        New-CsNetworkBandwidthPolicyProfile -Identity 10Mb_Link -Description "BW profile for 10Mb links" -AudioBWLimit 4000 -AudioBWSessionLimit 200 -VideoBWLimit 2800 -VideoBWSessionLimit 700
```
```    
        New-CsNetworkBandwidthPolicyProfile -Identity 50Mb_Link -Description "BW profile for 50Mb links" -AudioBWLimit 20000 -AudioBWSessionLimit 200 -VideoBWLimit 14000 -VideoBWSessionLimit 700
```
```    
        New-CsNetworkBandwidthPolicyProfile -Identity 25Mb_Link -Description "BW profile for 25Mb links" -AudioBWLimit 10000 -AudioBWSessionLimit 200 -VideoBWLimit 7000 -VideoBWSessionLimit 700
```

## Para criar perfis de política de largura de banda usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação à esquerda, clique em **Configuração da Rede**.

3.  Clique no botão de navegação **Perfil da Política**.

4.  Clique em **Novo**.

5.  Na página **Novo Perfil de Política**, clique em **Nome** e digite um nome para o perfil de política de largura de banda.

6.  Clique em **Limite de áudio** e digite o número máximo de kbps a ser permitido para todas as sessões de áudio combinadas.

7.  Clique em **Limite de sessão de áudio** e digite o número máximo de kbps a ser permitido para cada sessão de áudio individual.

8.  Clique em **Limite de vídeo** e digite o número máximo de kbps a ser permitido para todas as sessões de vídeo combinadas.

9.  Clique em **Limite de sessão de vídeo** e digite o número máximo de kbps a ser permitido para cada sessão de vídeo individual.

10. Opcionalmente, clique em **Descrição** e digite informações adicionais para descrever este perfil de política de largura de banda.

11. Clique em **Confirmar**.

12. Para concluir a criação de perfis de política de largura de banda para a sua topologia, repita as etapas de 4 a 11 com as configurações para outros perfis de política de largura de banda.

