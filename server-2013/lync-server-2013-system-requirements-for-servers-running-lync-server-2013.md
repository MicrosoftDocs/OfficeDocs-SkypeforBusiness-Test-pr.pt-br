---
title: 'Lync Server 2013: Requisitos de sistema para servidores executando Lync Server 2013'
TOCTitle: Requisitos de sistema para servidores executando Lync Server 2013
ms:assetid: 781d487d-5958-416a-becb-904d9af3cc0a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398588(v=OCS.15)
ms:contentKeyID: 49307173
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de sistema para servidores executando Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

> [!NOTE]  
> Para ver detalhes sobre os requisitos de hardware, consulte <a href="lync-server-2013-server-hardware-platforms.md">Plataformas de hardware de servidor para Lync Server 2013</a>.

Os servidores Standard Edition e Enterprise Edition compartilham os mesmos requisitos de software.

Os servidores que executam o Lync Server 2013 Enterprise Edition destinam-se à expansão até aproximadamente 80.000 usuários hospedados por pool. Os servidores que executam o Lync Server 2013 Standard Edition destinam-se a organizações menores e locais remotos da implantação da organização principal. Um par de servidores do Standard Edition pode dar suporte a até 5.000 usuários. Para ver detalhes sobre as diferenças entre os servidores Standard Edition e Enterprise Edition, consulte [Visão geral de implantação para Lync Server 2013](lync-server-2013-deployment-overview.md).

## Instalação do sistema operacional

> [!IMPORTANT]  
> O Lync Server 2013 está disponível apenas em uma edição de 64 bits, que exige um hardware de 64 bits e uma edição de 64 bits do sistema operacional Windows Server. Uma edição de 32 bits do Lync Server 2013 não está disponível com esta versão.

Os servidores Standard Edition e Enterprise Edition pode usar qualquer um dos seguintes:

  - Windows Server 2008 R2 SP1 ou Service Pack mais recente

  - Windows Server 2012

  - Windows Server 2012 R2

Instale o software do sistema operacional no servidor Standard Edition ou servidor front-end Enterprise Edition. Aplique todas as atualizações para que o sistema operacional fique com a última atualização e tenha um nível de atualização obrigatória consistente com os padrões da organização. Para obter mais detalhes sobre os requisitos operacionais, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de capacidade de suporte.

> [!NOTE]  
> Para que o Lync Server 2013 funcione no Windows Server 2012 R2, é necessário alterar o valor de uma chave do registro no Windows Server. Esta alteração pode ser necessária para que certificados funcionem corretamente e clientes se registrem nos Aparelho de Filial Persistente. Para obter mais informações, consulte <a href="http://support.microsoft.com/kb/2901554" class="uri">http://support.microsoft.com/kb/2901554</a>.

## Software adicional para Lync Server 2013

Além das atualizações necessárias para o sistema operacional, o Lync Server 2013 exige funções do sistema operacional, recursos e software para funcionar. Para obter detalhes sobre o software adicional que deve ser instalado antes de publicar sua topologia e instalar o Lync Server 2013, consulte [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) na documentação de Planejamento.

## Software adicional necessário para todas as funções de servidor

Em todas as funções de servidor, certifique-se de que o Interface da linha de comando do Windows PowerShell 3.0 e o Microsoft .NET Framework 4.5 estejam instalados.

Além disso, o Interface da linha de comando do Windows PowerShell 3.0 e o Microsoft .NET Framework 4.5 são obrigatórios em todos os computadores em que as ferramentas administrativas do Lync Server serão executadas.

## Windows PowerShell 3.0

O Lync Server 2013 exige a instalação do Windows PowerShell 3.0 em todos os computadores que farão parte da topologia do Lync Server. Para obter detalhes sobre a instalação do Windows PowerShell 3.0, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md).

> [!NOTE]  
> No Windows Server 2008 R2 com SP1, o Interface da linha de comando do Windows PowerShell 3.0 não pode ser instalado antes do Microsoft .NET Framework 4.5.

## Microsoft.NET Framework 4.5

Quando você instala o Microsoft .NET Framework 4.5 em servidores que executarão o Lync Server 2013 no Windows Server 2012 ou Windows Server 2012 R2, você deve executar uma etapa adicional. Após a instalação do .NET Framework 4.5, use o Gerenciador de Servidores para instalar a ativação HTTP.

**Para instalar a ativação HTTP do .NET 4.5 no Windows Server 2012 ou Windows Server 2012 R2**

1.  No menu **Iniciar** , clique em **Programas** , **Ferramentas Administrativas** e **Gerenciador de Servidores**.

2.  No Gerenciador de Servidores, em **Resumo dos Recursos** , selecione **Adicionar Recursos**.

3.  Expanda **.NET Framework 4.5**.

4.  Selecione a opção **Ativação de WCF** caso ainda não esteja selecionada. Em seguida, selecione **Ativação HTTP**.

5.  Clique em **Avançar** e siga os prompts para concluir a instalação.

