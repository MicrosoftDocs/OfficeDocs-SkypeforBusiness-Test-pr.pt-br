---
title: Editando o diagrama de configuração de rede no Lync Server 2013
TOCTitle: Editando o diagrama de configuração de rede no Lync Server 2013
ms:assetid: 47425ab1-5645-4d6f-b202-64bcce43e3ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558643(v=OCS.15)
ms:contentKeyID: 52057617
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Editando o diagrama de configuração de rede no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

A maior parte do trabalho que um designer executa na Lync Server 2013, Ferramenta de Planejamento consiste em definir as entradas para os endereços IP e FQDNs (nomes de domínio totalmente qualificados) para as entradas no diagrama de rede. As informações inseridas nessa página são transferidas para os relatórios e outras informações contidas no Ferramenta de Planejamento.

![Diagrama da Rede de ferramentas de planejamento](images/Gg558643.eeabee2d-698c-4b79-baa5-caa4cfb7edb3(OCS.15).jpg "Diagrama da Rede de ferramentas de planejamento")

O Ferramenta de Planejamento cria um diagrama de rede com texto padrão para endereços IP e FQDNs.

Para editar os valores de entrada e diagrama de rede:

1.  Escolha uma seção da rede para começar o trabalho. Por exemplo, clique duas vezes no texto, **rp01.contoso.net**. Na caixa de diálogo que for aberta, digite o FQDN real do servidor access1.contoso.com e o endereço IP real, substituindo o 131.107.155.3.access1.contoso.com.

2.  Clique em **OK** para salvar as entradas.

3.  Continue a editar os endereços IP e os FQDNs, fornecendo endereços IP virtuais para balanceadores de carga de hardware ou entradas de servidor para balanceamento de carga do DNS (Sistema de Nome de Domínio) para servidores em pools.

Um recurso útil da Ferramenta de Planejamento é que ela pode atribuir incrementalmente um intervalo de endereços IP e nomes de host do servidor, em vez de exigir que o designer edite cada servidor separado em um pool. Por exemplo:

1.  Clique duas vezes nos Servidores Front-End em pool. Quando a caixa de diálogo for aberta, selecione **Deseja usar os IPs e o FQDN como pontos de partida para todos os servidores equivalentes neste cluster?**.

2.  Por exemplo, o valor inicial para o primeiro servidor é fe0101.contoso.com e um endereço IP de 192.168.21.122.

3.  Digite **fe0.contoso.com** em **FQDN do Servidor Front-End**, digite **192.168.21.131** em **Endereço IP do Servidor Front-End** e clique em **OK**.

4.  O recurso de incremento automático atualiza todos os servidores no pool para fe01 até fe06 e todos os endereços IP de 192.168.21.131 até 136.

Após ter concluído todas as edições, salve a topologia completando as seguintes etapas:

Para salvar o design do Ferramenta de Planejamento, clique em **Arquivo**, **Salvar Topologia** ou **Salvar Topologia como**. Se uma caixa de diálogo **Salvar Ferramenta de Planejamento como** for exibida, digite um nome para o arquivo em **Nome do arquivo** e clique em **Salvar**.

## Consulte Também

#### Conceitos

[Editando o design no Lync Server 2013](lync-server-2013-editing-the-design.md)

