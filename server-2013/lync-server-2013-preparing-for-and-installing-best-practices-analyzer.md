---
title: Preparando e Instando o Analisador de Práticas Recomendadas
TOCTitle: Preparando e Instando o Analisador de Práticas Recomendadas
ms:assetid: 550613dd-dc08-482e-9980-a3fe187cd162
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg591347(v=OCS.15)
ms:contentKeyID: 49306740
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando e Instando o Analisador de Práticas Recomendadas

 

_**Tópico modificado em:** 2016-12-08_

Você deve estar conectado como um membro do grupo Administradores para executar as tarefas que estão descritas neste tópico.

## Os requisitos de sistema para a instalação do Analisador de Práticas Recomendadas

Para executar o Lync Server 2013, o Analisador de Práticas Recomendadas para examinar o seu ambiente, o computador deve estar executando uma edição de 64 bits de um ou mais dos seguintes sistemas operacionais:

  - O sistema operacional Windows Server 2008 R2 com o Service Pack 1 (SP1) Standard

  - O sistema operacional Windows Server 2008 R2 com o SP1 Enterprise

  - O sistema operacional Windows Server 2008 R2 com o SP1 Datacenter

  - O sistema operacional Windows Server 2012 Datacenter

  - O sistema operacional Windows Server 2012 Standard

  - O sistema operacional Windows Server 2012 Enterprise

  - Sistema Operacional do Datacenter do Windows Server 2012 R2

  - Sistema Operacional Padrão do Windows Server 2012 R2

  - Sistema Operacional do Enterprise do Windows Server 2012 R2

  - O sistema operacional Windows 8

  - O sistema operacional Windows 7

O computador também deve estar executando o seguinte:

  - Microsoft .NET Framework 4.5. Para o Lync Server 2013, você deve instalar manualmente a edição de 64 bits do Microsoft .NET Framework 4.5 no servidor antes de instalar Lync Server 2013.

  - Lync Server 2013, Componentes Principais.

  - Pacote de compatibilidade com versões anteriores da WMI. Para obter detalhes, consulte [Instalar o pacote de Compatibilidade com Versões Anteriores](install-wmi-backward-compatibility-package.md) na Documentação de migração.

  - Windows PowerShell 3.0. Para obter detalhes, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md) na Documentação de implantação.

Você pode instalar o Analisador de Práticas Recomendadas nos computadores com um sistema operacional suportado que não esteja executando o Lync Server 2013, Componentes Principais ou Pacote de compatibilidade com versões anteriores da WMI, mas é possível utilizar o Analisador de Práticas Recomendadas nesses computadores somente para visualizar relatórios, não para executar verificações.

## Escolhendo um computador para instalação

Recomendamos que você instale o Lync Server 2013, o Analisador de Práticas Recomendadas em um computador que está dedicado ao gerenciamento do Lync Server 2013. Você pode instalar a ferramenta em um servidor executando o Lync Server 2013 ou um computador administrativo executando ferramentas administrativas do Lync Server 2013. Se você instalar a ferramenta em um servidor que esteja executando o Lync Server, recomendamos que você utilize a ferramenta para examinar somente esse servidor.

## Instalando o Analisador de Práticas Recomendadas

Você pode fazer download do Analisador de Práticas Recomendadas para o Lync Server 2013 em [http://go.microsoft.com/fwlink/?linkid=266539\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=266539%26clcid=0x416).

Para instalar o Analisador de Práticas Recomendadas, inicie o arquivo RtcBPA.msi do Arquivo Microsoft Installer (.msi) no computador no qual você deseja instalar a ferramenta e, em seguida, siga as instruções na tela. A localização padrão para instalação dos arquivos de programas é *\<system drive\>*\\Program Files\\Lync Server 2013\\BPA.

