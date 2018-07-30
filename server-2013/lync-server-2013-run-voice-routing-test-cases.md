---
title: Executar casos de teste de roteamento de voz no Lync Server 2013
TOCTitle: Executar casos de teste de roteamento de voz no Lync Server 2013
ms:assetid: fb4d32df-b9ea-4944-8cd7-a6102c78c465
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413068(v=OCS.15)
ms:contentKeyID: 49308689
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executar casos de teste de roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-24_

Você pode executar todos os casos de teste no seu pacote de casos de teste de roteamento de voz ou pode executar um ou mais casos de teste selecionados.

## Para executar todos os casos de teste de roteamento de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de voz** e em **Testar roteamento de voz**.

4.  Na página **Testar roteamento de voz**, clique em **Ação** e em **Executar todos**.
    
    O status de aprovação ou reprovação de cada caso de teste é exibido na coluna **Aprovado/reprovado**. Se um caso de teste ainda não foi executado, N/D é exibido na coluna **Aprovado/reprovado**.

5.  (Opcional) Para ver os resultados detalhados para cada caso de teste, clique duas vezes no nome do caso de teste. Os resultados são exibidos na área acinzentada no lado direito da página **Editar caso de teste**:
    
    1.  **Resultado do teste:** Status de aprovação ou reprovação geral da execução do caso de teste.
    
    2.  **Regra de normalização:** A primeira regra de normalização no plano de discagem selecionada para este caso de teste que corresponde ao número discado (o valor no campo **Número para teste**).
    
    3.  **Número normalizado:** O valor do número discado após a regra de normalização ter traduzido-o.
    
    4.  **Primeiro uso de PSTN:** O registro de primeiro uso do Rede Telefônica Pública Comutada (PSTN) na política de voz selecionada para este caso de teste que corresponde o número discado.
    
    5.  **Primeiro roteamento:** O primeiro roteamento de voz no primeiro registro de uso do PSTN que corresponde o número discado.
        
        > [!NOTE]  
        > Os campos <strong>Registro de uso PSTN esperado</strong> e <strong>Roteamento esperado</strong> são opcionais na configuração do caso de teste de roteamento de voz. Se o caso de teste não especificar estes valores, o campo correspondente nos resultados de teste estarão vazios.

## Para executar um ou mais casos de teste de roteamento de voz selecionados

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e em **Testar roteamento de voz**.

4.  Na página **Testar roteamento de voz** , clique nos nomes dos casos de teste que você deseja executar.

5.  No menu **Ação** , clique em **Executar selecionado**.
    
    O status de aprovação ou reprovação de cada caso de teste é exibido na coluna **Aprovado/reprovado**. Se um caso de teste ainda não foi executado, N/D é exibido na coluna **Aprovado/reprovado**.

6.  (Opcional) Para ver os resultados detalhados para cada caso de teste, clique duas vezes no nome do caso de teste. Os resultados são exibidos na área acinzentada no lado direito da página **Editar caso de teste**:
    
    1.  **Resultado do teste:** Status de aprovação ou reprovação geral da execução do caso de teste.
    
    2.  **Regra de normalização:** A primeira regra de normalização no plano de discagem selecionado para este caso de teste que corresponde ao número discado (o valor no campo **Número para teste**).
    
    3.  **Número normalizado:** O valor do número discado após a regra de normalização ter traduzido-o.
    
    4.  **Primeiro uso de PSTN:** O registro de primeiro uso do PSTN na política de voz selecionada para este caso de teste que corresponde o número discado.
    
    5.  **Primeiro roteamento:** O primeiro roteamento de voz no primeiro registro de uso do PSTN que corresponde o número discado.
        
        > [!NOTE]  
        > Os campos <strong>Registro de uso PSTN esperado</strong> e <strong>Roteamento esperado</strong> são opcionais na configuração do caso de teste de roteamento de voz. Se o caso de teste não especificar estes valores, o campo correspondente nos resultados de teste estarão vazios.

## Consulte Também

#### Outros Recursos

[Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)  
[Executando testes de roteamento de voz no Lync Server 2013](lync-server-2013-running-voice-routing-tests.md)

