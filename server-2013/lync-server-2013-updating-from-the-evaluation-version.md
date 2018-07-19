---
title: Atualizando a versão de avaliação do Lync Server 2013
TOCTitle: Atualizando a versão de avaliação do Lync Server 2013
ms:assetid: 62a88180-4289-4a2a-9cb9-1b9899344a63
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521005(v=OCS.15)
ms:contentKeyID: 49306904
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atualizando a versão de avaliação do Lync Server 2013

 

_**Tópico modificado em:** 2012-06-20_

Se você tiver instalado a versão de avaliação do Microsoft Lync Server 2013, com o tempo, precisará atualizar essa instalação para uma cópia licenciada do software. Isso ocorre porque a versão de avaliação expira 180 dias depois de instalada. Entretanto, não será preciso desinstalar completamente a versão de avaliação e depois instalar a versão licenciada. Em vez disso, depois de obter uma chave de licença válida, você poderá atualizar a versão de avaliação do Lync Server 2013 executando o procedimento a seguir em cada computador que atua como Lync Server Servidor Front-End, Diretor ou Servidor de Borda. Não é preciso atualizar computadores executando outras funções de servidor, como um Servidor de Monitoramento ou um Servidor de Arquivamento.

## Atualizando da versão de avaliação do Microsoft Lync Server 2013

Para atualizar um computador da versão de avaliação do Lync Server 2013 para a versão licenciada do software:

**Atualizando da versão de avaliação do Microsoft Lync Server 2013**

1.  Faça logon no computador como um administrador local.

2.  Clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  No Shell de Gerenciamento do Lync Server, digite o seguinte comando e pressione ENTER:
    
        msiexec.exe /fvomus server.msi EVALTOFULL=1 /qb
    
    Talvez seja necessário especificar o caminho completo para o arquivo server.msi. Esse arquivo pode ser encontrado na pasta Setup dos arquivos de instalação na mídia de volume do Lync Server.

4.  Após a conclusão da instalação, digite o seguinte no prompt de comando e pressione ENTER:
    
        Enable-CsComputer

5.  Repita esse procedimento em qualquer outro Servidor Front-End, Diretor ou Servidor de Borda executando uma cópia de avaliação do Lync Server. Esse procedimento também deve ser executado em todos os servidores de filiais que foram implantados com o uso dos arquivos de instalação de mídia do Lync Server.

Se você não tiver certeza se a versão de avaliação do Lync Server está sendo executada em determinado computador, poderá confirmar isso executando o seguinte comando a partir do Shell de Gerenciamento do Lync Server:

    Get-CsServerVersion

O cmdlet [Get-CsServerVersion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsServerVersion) analisará o computador local e o relatará o seguinte:

  - Que a chave de licença de volume do Lync Server foi instalada no computador, o que significa que nenhuma atualização é necessária.

  - Que a chave de licença de avaliação do Lync Server foi instalada, o que significa que o computador deve ser atualizado.

  - Que nenhuma chave de licença de volume é necessária no computador. A atualização da versão de avaliação para a versão licenciada só é necessária em servidores Front-End, Diretores e Servidores de Borda.

