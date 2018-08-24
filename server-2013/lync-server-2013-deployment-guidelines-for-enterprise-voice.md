---
title: 'Lync Server 2013: Orientações de implantação para Enterprise Voice'
TOCTitle: Orientações de implantação para Enterprise Voice
ms:assetid: 8985bd93-7613-4cef-9c89-51df6049ed9b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398694(v=OCS.15)
ms:contentKeyID: 49307391
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Orientações de implantação para Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Este tópico descreve os pré-requisitos e outras diretrizes que devem ser levadas em conta durante o planejamento da implantação do Lync Server 2013 e da carga de trabalho do Enterprise Voice.

## Pré-requisitos da Implantação

Para que a experiência de implantação do Enterprise Voice seja ideal, verifique se a infraestrutura de TI, a rede e os sistemas atendem aos seguintes pré-requisitos:

  - O Lync Server 2013 Standard Edition ou Enterprise Edition está instalado e funcionando na sua rede.

  - Todos os Servidores de Borda estão implantados e operando na rede de perímetro, incluindo os Servidores de Borda com o Serviço de Borda de Acesso, o Serviço de Borda A/V, o Serviço de Borda de Webconferência e um proxy reverso.

  - Um ou mais usuários foram criados e habilitados para o Lync Server.

  - O Microsoft Exchange Server 2007 Service Pack 1 (SP1), o service pack mais recente ou o Microsoft Exchange Server 2010 deve estar instalado. É necessário ter um dos arquivos para integrar o Unificação de Mensagens (UM) do Exchange ao Lync Server, fornecer notificações avançadas e chamar as informações de log para os pontos de extremidade do cliente.

  - Um número de telefone principal exclusivo foi designado, normalizado e copiado ao atributo **msRTCSIP-line** de cada usuário que deve ser habilitado para o Enterprise Voice.
    
    > [!NOTE]  
    > O Lync Server oferece suporte a números E.164 e Discagem Interna não Direta (DID). Os números não DID podem ser representados no formato <strong>&lt;E.164&gt;;ext=&lt;extension&gt;</strong> ou como uma seqüência de dígitos, com o requisito de que a extensão particular é exclusiva na empresa. Por exemplo, um número particular de 1001 pode ser representado como <strong>+1425550100;ext=1001</strong>, ou como <strong>1001</strong>. Quando representado como <strong>1001</strong>, a expectativa é de que esse número particular seja exclusivo na empresa.

  - Os administradores responsáveis pela implantação do Enterprise Voice devem ser membros do grupo RTCUniversalServerAdmins.

  - No mínimo, o Office Communicator 2007 é implantado com êxito. Para usar os recursos novos para esta versão, o Lync 2013 é implantado.

  - A Infraestrutura de chave gerenciada (MKI) é implantada e configurada usando uma infraestrutura da autoridade de certificação (CA) de terceiros ou da Microsoft.

  - Cada computador no qual o Servidor de Mediação será instalado deve ser:
    
      - Um servidor membro de um domínio e preparado para o Serviços de Domínio Active Directory. Para os procedimentos de preparação do Serviços de Domínio Active Directory, consulte [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) na documentação de implantação.
    
      - Executando um dos seguintes sistemas operacionais:
        
           A edição de 64 bits do sistema operacional Windows Server 2008 Standard
        
           A edição de 64 bits do sistema operacional Windows Server 2008 Enterprise

  - Se a conexão ao PBX ou PSTN ocorrer por meio de uma conexão de TDM (multiplexação de divisão de tempo), um ou mais gateways PSTN estarão disponíveis para implantação. Se a conexão ocorrer por meio de um tronco SIP, não é necessário ter um gateway PSTN.

## Interrupções de energia, da rede ou dos serviços telefônicos

Se houver uma paralisação, interrupções ou outra degradação da energia, rede ou ods serviços de telefone local, a voz, as mensagens instantâneas, a presença e outros recursos de Lync Server e qualquer dispositivo conectado a Lync Server pode não funcionar adequadamente.

## O Enterprise Voice depende da disponibilidade do servidor e da operabilidade do hardware e do cliente VoIP

As comunicações com voz através do Lync Server dependem da disponibilidade do software do servidor, bem como do funcionamento adequado dos clientes de voz ou dos dispositivos telefônicos de hardware conectados a esse software.

## Meios alternativos de acessar serviços de emergência

Para os locais onde for necessário instalar um cliente de voz (por exemplo, um PC executando o cliente Lync ou um dispositivo de Lync Phone Edition), recomendamos manter uma opção de backup para que os usuários chamem os serviços de emergência (por exemplo, 901) no caso de uma falha de energia, redução de conectividade de rede, paralisação do serviço de telefonia ou outro problema que pode inibir a operação de Lync Server, Lync ou dos dispositivos Lync Phone Edition. Tais opções alternativas poderiam incluir um telefone conectado a uma linha de PSTNpadrão ou um telefone celular.

## Chamadas de emergência e sistemas telefônicos de várias linhas

O uso de um sistema telefônico de várias linhas (MLTS) pode estar sujeito às leis federais dos EUA ou às leis de outros países/regiões que requerem que o sistema MLTS forneça o número de telefone do chamador, a extensão e/ou o local físico para os serviços de emergência aplicáveis quando um chamador chama serviços de emergência (por exemplo, ao discar um número de acesso de emergência, como 901). Nesta versão, o Lync Server pode ser configurado para fornecer o local físico do chamador para um provedor de serviços de emergência, conforme descrito em [Planejamento para serviços de emergência (E9-1-1) no Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md). A conformidade com as leis de MLTS é de responsabilidade exclusiva do comprador de dispositivos Lync Server, cliente Lync e dispositivos Lync Phone Edition devices.

