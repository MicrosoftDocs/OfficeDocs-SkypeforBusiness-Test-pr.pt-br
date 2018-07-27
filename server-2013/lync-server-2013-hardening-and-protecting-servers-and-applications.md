---
title: 'Lync Server 2013: Protegendo servidores e aplicativos'
TOCTitle: Protegendo servidores e aplicativos para Lync Server 2013
ms:assetid: 9ca2b233-26f1-4d72-96e7-81a82c727806
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518331(v=OCS.15)
ms:contentKeyID: 60505937
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Protegendo servidores e aplicativos para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Você deve proteger o sistema operacional e os aplicativos com base nas práticas recomendadas desse componente específico. Esta seção descreve como aumentar a segurança dos servidores de aplicativo e usar a Política de Grupo para implementar bloqueios de segurança.

> [!NOTE]  
> Você também pode proteger os bancos de dados usados na implementação do Microsoft Lync Server 2013. Para obter informações detalhadas, consulte <a href="lync-server-2013-hardening-and-protecting-databases.md">Protegendo os bancos de dados do Lync Server 2013</a>.

## Protegendo servidores de aplicativo

No caso dos servidores de aplicativos, o sistema operacional e o aplicativo devem ser protegidos. Por exemplo, um computador com o Windows Server 2008 dedicado à execução do Microsoft Internet Security and Acceleration (ISA) Server 2006 deve ser protegido sob a perspectiva do sistema operacional e do aplicativo. Minimizar o número de serviços em execução e fornecidos pelo servidor deve ser o objetivo principal.

## Protegendo servidores virtuais

Os instantâneos de servidor virtual contêm cópias dos discos de dados do servidor e despejos dos dados da memória, ambos podendo conter dados criptográficos confidenciais que podem resultar em ataques. No caso dos servidores de produção implementados por meio da virtualização, você deve desabilitar todos os instantâneos do servidor ou gerenciá-los de modo controlado. Para obter informações detalhadas sobre como proteger os servidore virtuais Hyper-V, consulte o Guia de Segurança do Hyper-V em: [http://go.microsoft.com/fwlink/p/?LinkId=214176](http://go.microsoft.com/fwlink/p/?linkid=214176).

## Política de Grupo

No Windows Server 2008 e no Windows Server 2008 R2, a Política de Grupo fornece gerenciamento de configurações de desktop baseado em diretórios. Você pode usar a Política de Grupo para implementar bloqueios de segurança definindo as configurações de Computador e Usuário em um Objeto de Política de Grupo (GPO):

  - Políticas baseadas no Registro

  - Segurança

  - Instalação do software

  - Scripts

  - Redirecionamento de pasta

  - Serviços de instalação remota

Para fornecer uma interface do usuário para que o administrador defina essas configurações, são enviados modelos administrativso com as versões de sistema operacional, versões de service pack e alguns aplicativos, incluindo o Lync Server 2013.

O arquivo Communicator.adm é um modelo administrativo enviado com o Lync Server 2013. Ele é instalado no diretório *%windir%*\\inf\\ e faz a interface com as configurações da Política de Grupo. Cada configuração no Communicator.adm corresponde a uma configuração no Registro que afeta o comportamento do aplicativo.

As configurações podem ser acessadas no GPedit.dll, que está disponível no console de usuários e computadores do Active Directory e no Console de Gerenciamento de Política de Grupo (GPMC).

## Configurações de segurança da Política de Grupo

A Política de Grupo contém as configurações de segurança de um GPO em Computer Configuration/Windows Settings/Security Settings quando acessado no GPedit.dll. Você pode importar modelos de segurança para definir as configurações de segurança do GPO. O Guia de Segurança do Windows Server 2008 em [http://go.microsoft.com/fwlink/p/?LinkId=145186](http://go.microsoft.com/fwlink/p/?linkid=145186) e o Windows Server 2008 R2 Security Compliance Management Toolkit em [http://go.microsoft.com/fwlink/p/?LinkId=211882](http://go.microsoft.com/fwlink/p/?linkid=211882) oferecem diveresos modelos que você pode modificar de acordo com suas necessidades.

## Práticas recomendadas

  - Proteja todos os sistemas operacionais de servidor e aplicativos.

  - Proteja os instantâneos de servidor e aprimore a segurança de todos os servidores virtuais.

  - Use a Política de Grupo para implementar bloqueios de segurança.

