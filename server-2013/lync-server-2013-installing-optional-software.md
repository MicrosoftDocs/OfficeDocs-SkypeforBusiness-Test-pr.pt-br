---
title: 'Lync Server 2013: Instalando software opcional'
TOCTitle: Instalando software opcional
ms:assetid: b95b3301-fa1e-4b96-9af4-05b43d39db8d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615032(v=OCS.15)
ms:contentKeyID: 52057698
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando software opcional no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

A Microsoft Lync Server 2013, Ferramenta de Planejamento foi desenvolvida para exportar para Microsoft Excel e Microsoft Visio. Apesar dessas aplicações não serem obrigatórias para a operação da Ferramenta de Planejamento, elas agregam bastante valor à implantação e documentação do seu design.

## Software opcional

## Microsoft Excel

Exportar seu design para Microsoft Excel cria um relatório que exibe sete guias na planilha:

  - Resumo - Exibe informações sobre a configuração de site, incluindo conta de usuário, configurações de capacidade e informações sobre o perfil do servidor.

  - Perfil de hardware - Exibe um relatório das configurações de hardware recomendadas para servidores especificados na topologia, incluindo CPU, memória, disco e interface de rede. Também está incluída a quantidade e especificações recomendadas para os componentes do servidor. Cada servidor também é definido por site, para fornecer uma representação completa dos requisitos de servidor por cada site.

  - Requisitos de portas - Exibe um relatório de todas as portas habilitadas, além da associação com DNS LB (balanceamento de carga DNS) e HLB (balanceadores de carga de hardware). Esse relatório deve ser usado para planejar suas configurações de firewall e DNS LB e HLB.

  - Relatório de Resumo - exibe o resumo geral das definições requeridas para que se possa configurar a sua rede Servidor de Borda.

  - Relatório de certificados - exibe o nome do sujeito e seus nomes alternativos que, são requeridos para os certificados necessários para a execução do Servidores de Borda.

  - Relatório do firewall - exibe as portas de origem e destino e endereços IP para as interfaces internas e externas.

  - Relatório de DNS - exibe o nome de domínio totalmente qualificado (FQDN) e endereços IP/VIP requeridos para cada entrada DNS que você criar.

## Microsoft Visio

Exportar seu design para o Microsoft Visio cria um diagrama para ser usado com seus objetivos de documentação de sua topologia e infraestrutura configuradas. O diagrama importado pode ser editado e reorganizado a fim de atender às suas necessidades de documentação. O diagrama típico do Visio incluirá:

> [!NOTE]  
> Se seu design for grande o suficiente para exigir mais de três Servidores Front-End, uma página adicional será criada para o Pool de Front-Ends, Servidores Front-End, o computador executando o SQL Server, endereços IP e FQDNs.

  - Topologia global - Diagrama de sites configurados do Lync Server 2013.

  - Guia Nome do Site - Exibe a topologia de configuração do site com Servidor de Borda, firewall, PSTN (Rede Telefônica Pública Comutada) com gateways e a implantação do servidor interna. A implantação interna é composta por servidores e pools configurados, incluindo os pools Front-End, servidores com base no SQL Server, Serviços de Domínio Active Directory, Diretores, servidores UM (Mensagem Unificada) do Exchange, servidores de Caixa de Correio do Exchange, Office Web Apps Servers, Servidor de Mediação e Servidores de Chat Persistente.

  - Diagrama de rede de borda - Diagrama detalhando a configuração do Servidor de Borda com endereços IP associados e FQDNs. Balanceamento de carga de DNS e balanceadores de carga de hardware também estão incluídos. Além disso, os Diretores e o Servidor Front-End ou então o Pool de Front-Ends são exibidos, com DNS LB ou HLB associados e o endereço IP (o Ferramenta de Planejamento suporta ambos os endereços IPv4 e IPv6) e o FQDN atribuídos.

## Consulte Também

#### Tarefas

[Instalando a Ferramenta de Planejamento no Lync Server 2013](lync-server-2013-installing-the-planning-tool.md)

