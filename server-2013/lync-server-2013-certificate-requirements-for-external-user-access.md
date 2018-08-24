---
title: 'Lync Server 2013: Requisitos de certificado para acesso do usuário externo'
TOCTitle: Requisitos de certificado para acesso do usuário externo
ms:assetid: d45b6b10-556f-4b10-b1a7-fb0d0a64a498
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398920(v=OCS.15)
ms:contentKeyID: 49308228
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de certificado para acesso do usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013  software de comunicação suporta o uso de um único certificado público para interfaces externas de Borda de acesso e webconferência, além do serviço Autenticação A/V. A interface interna de Borda normalmente usa um certificado privado emitido por uma autoridade de certificação (CA) interna, mas também pode usar um certificado público, contanto que seja de uma CA pública confiável. O proxy reverso em sua implantação usa um certificado público e criptografa a comunicação do proxy reverso para os clientes e do proxy reverso para os servidores internos usando HTTP (ou seja, Segurança da camada de transporte sobre HTTP).

Veja a seguir os requisitos para o certificado público usado para interfaces externas de Borda de acesso e de webconferência e para o serviço de autenticação A/V:

  - O certificado precisa ser emitido por uma CA pública aprovada que suporta nomes de entidade alternativos. Para obter detalhes, consulte o artigo 929395 da Base de Conhecimento da Microsoft, "Parceiros de certificado de comunicações unificados para Exchange Server e servidor de comunicação" em [http://go.microsoft.com/fwlink/p/?linkId=202834](http://go.microsoft.com/fwlink/p/?linkid=202834).

  - Se o certificado for usado em um pool de Borda, ele deverá ser criado como exportável, com o mesmo certificado usado em cada Servidor de Borda no pool de Borda. O requisito de chave privada exportável serve para o serviço de Autenticação A/V, que precisa usar a mesma chave privada em todos os Servidores de Borda no pool.

  - Se você deseja maximizar o tempo para seus serviços de Áudio/Vídeo, revise os requisitos de certificado para implementar um certificado do Serviço de Borda A/V não acoplado (isto é, um certificado do Serviço de Borda A/V separado de outros fins de certificado da Borda Externa). Para obter detalhes, consulte [Alterações no Lync Server 2013 que afetam o planejamento do Servidor de Borda](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md), [Planejar certificados do Servidor de Borda no Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md) e [Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate).

  - O nome do assunto do certificado é o FQDN da interface externa do Serviço de Borda de Acesso ou o VIP do balanceador de carga de hardware (por exemplo, access.contoso.com).
    
    > [!NOTE]  
    > Para o Lync Server 2013, isso não é mais um requisito, mas ainda é recomendado para compatibilidade com o Office Communications Server.

  - A lista de nomes de entidade alternativos contém os FQDNs do seguinte:
    
      - A interface externa do Serviço de Borda de Acesso ou o VIP do balanceador de carga de hardware (por exemplo, sip.contoso.com).
        
        > [!NOTE]  
        > Embora o nome de entidade do certificado seja igual ao FQDN da Borda de acesso, o nome de entidade alternativo também precisa conter o FQDN da Borda de acesso, pois a TLS ignora o nome de entidade e usa as entradas de nome de entidade alternativo para validação.    
      - Da interface externa da Borda de webconferência ou VIP do balanceador de carga de hardware (por exemplo, webcon.contoso.com).
    
      - Se você estiver usando a configuração ou federação automática de cliente, inclua também quaisquer FQDNs de domínio de SIP usados em sua empresa (por exemplo, sip.contoso.com, sip.fabrikam.com).
    
      - O Serviço de Borda A/V não usa o nome do assunto ou as entradas de nomes alternativos do assunto.
    
    > [!NOTE]  
    > A ordem dos FQDNs na lista de nomes de entidade alternativos não importa.

Se você estiver implantando múltiplos Servidores de Borda com carga balanceada em um site, o certificado do serviço de autenticação A/V instalado em cada Servidor de Borda deverá ser da mesma CA e deverá usar a mesma chave privada. Observe que a chave privada do certificado precisa ser exportável, independentemente se for usada em um Servidor de Borda ou em muitos Servidores de Borda. Também deve ser exportável se você solicitar o certificado de qualquer computador além do Servidor de Borda. Como o serviço de autenticação A/V não usa o nome de entidade ou o nome alternativo de entidade, é possível reutilizar o certificado de Borda de acesso contanto que os requisitos de nome de entidade e de nome de entidade alternativo sejam atendidos para a Borda de acesso e para a Borda de webconferência e a chave privada do certificado seja exportável.

Os requisitos para o certificado privado (ou público) usado na interface interna de Borda são os seguintes:

  - O certificado pode ser emitido por uma CA interna ou uma CA de certificado público aprovada.

  - O nome de entidade do certificado é normalmente o FQDN da interface interna da Borda ou o VIP do balanceador de carga de hardware (por exemplo, lsedge.contoso.com). No entanto, é possível usar um certificado curinga na Borda interna.

  - Nenhuma lista de nomes de entidade alternativos é necessária.

O proxy reverso em seus serviços de implantação solicitam:

  - Acesso de usuário externo para atender ao conteúdo das reuniões

  - Acesso de usuário externo para expandir e exibir membros dos grupos de distribuição

  - Acesso de usuário externo para arquivos baixáveis do Serviço de Catálogo de Endereços

  - Acesso de usuário externo ao cliente do Lync Web App

  - Acesso de usuário externo à página da web Configurações de Conferência Discada

  - Acesso de usuário externo ao Serviço de Informações de Local

  - Acesso de dispositivo externo ao Serviço de Atualização de Dispositivo e obtenção de atualizações

O proxy reverso publica as URLs de Componentes da web do servidor interno. As URLs dos Componentes da web são definidas no Diretor, Servidor Front-End ou no Pool de Front-Ends como os **Serviços da web externos** no Construtor de Topologias.

Entradas curinga são suportadas no campo de nome de entidade alternativo do certificado atribuído ao proxy reverso. Para obter detalhes sobre como configurar a solicitação de certificado para o proxy reverso, consulte [Solicitar e configurar um certificado para seu proxy HTTP reverso no Lync Server 2013](lync-server-2013-request-and-configure-a-certificate-for-your-reverse-http-proxy.md).

## Consulte Também

#### Conceitos

[Suporte a certificado curinga no Lync Server 2013](lync-server-2013-wildcard-certificate-support.md)

