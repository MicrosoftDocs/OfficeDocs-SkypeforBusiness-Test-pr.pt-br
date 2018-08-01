---
title: 'Lync Server 2013: Coleta de dados'
TOCTitle: Coleta de dados
ms:assetid: e40b03e5-455d-4bbc-831a-c61b1380db53
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399008(v=OCS.15)
ms:contentKeyID: 49308407
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Coleta de dados no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

No Microsoft Lync Server 2013  software de comunicação, é possível executar o Microsoft Lync Server 2013, Ferramenta de Planejamento sem documentar os endereços IP e os FQDNs (nomes de domínio totalmente qualificado) do Servidor de Borda existentes e propostos, mas é muito mais difícil fazer isso sem causar erros de configuração. Por exemplo, se for necessária uma coexistência durante um período, um erro comum é reutilizar os FQDNs de uma implantação de Borda existente na implantação de Borda do Lync Server 2013. Tendo endereços IP existentes e propostos e FQDNs gravados em uma planilha, tabela ou outro formato visual, você ajuda a evitar problemas de configuração durante a instalação.


> [!WARNING]  
> Se você usou versões anteriores do Ferramenta de Planejamento, pode ter usado a ferramenta para criar sua topologia e exportado o documento de topologia para uso no Construtor de Topologias para publicar sua topologia. A capacidade de exportar a topologia foi removida do Ferramenta de Planejamento. Usar uma versão anterior do Ferramenta de Planejamento para criar um documento de topologia para o Lync Server 2013 não é recomendado e produzirá resultados inesperados;



Portanto, a abordagem recomendada é usar o seguinte modelo de coleta de dados, que corresponde à sua topologia de Borda, para coletar os diversos FQDN e endereços IP que precisam ser inseridos no Ferramenta de Planejamento. Ao documentar a configuração atual e proposta, é possível colocar os valores no contexto apropriado para seu ambiente de produção. Você é forçado a pensar sobre como configurará a coexistência e os novos recursos, como URLs simples, compartilhamentos de arquivo, Servidores de Conferência A/V dedicados e balanceamento de carga DNS.

Para implantar com sucesso o Microsoft Lync Server 2013, você precisa compreender a interação e a confiança de componentes individuais. Ao coletar dados da sua rede existente e infraestrutura do servidor e aplicar as diretrizes nestas seções, é possível integrar os componentes do Lync Server 2013  Servidor de Borda em sua infraestrutura.

Introduzido no [Escolhendo uma topologia no Lync Server 2013](lync-server-2013-choosing-a-topology.md), existem três arquiteturas principais com duas variações, para um total de cinco cenários de implantação possíveis. Um destes cenários será o ponto inicial da sua coleta de dados. O endereço IP, nome do servidor e de domínio são exemplos que coincidem com o certificado, firewall e diagramas DNS que detalham a informação necessária para uma solução de planejamento completa. Os diagramas e preenchimento no seu certificado necessário, valores de DNS e firewall são especialmente importantes em comunicações entre equipes onde o gerenciamento da autoridade de certificação, configuração de firewall e DNS é gerenciado por equipes diferentes da equipe que planeja a implantação. O diagrama oferece informações sobre os componentes necessários que podem ser usados para comunicar estes requisitos para a colaboração entre equipes.

Os diagramas oferecidos são genéricos intencionalmente, mas permitem a coleta de todos os dados pertinentes que serão necessários para comunicação dos requisitos em um cenário de várias equipes onde a rede, firewall, criação e gerenciamento de certificados, implantação do servidor e gerenciamento do servidor são tratados por grupos diferentes. Com os detalhes necessários para configuração de rede, firewalls, portas e protocolos, certificados e servidores não tem valor quando a implantação do Lync Server está em andamento.

**Servidor de Borda e Pool de borda**

![Servidor de Borda e Pool de Borda](images/Gg399008.7624717a-ce99-4ae8-a929-2c4d74a2e47d(OCS.15).jpg "Servidor de Borda e Pool de Borda")

**Proxy Reverso**

![Proxy reverso](images/Gg399008.cf63fc50-2d11-4334-afc8-2d664ba1b6bb(OCS.15).jpg "Proxy reverso")

**Diretor ou Pool de diretores**

![Diretor e Pool de Diretores](images/Gg399008.56ba29ff-1309-4d5d-bf5c-35372169e947(OCS.15).jpg "Diretor e Pool de Diretores")

