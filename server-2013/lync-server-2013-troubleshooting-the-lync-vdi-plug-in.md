---
title: Resolução de problemas no Plug-in Lync VDI no Lync Server 2013
TOCTitle: Resolução de problemas no Plug-in Lync VDI no Lync Server 2013
ms:assetid: 183c9449-b907-409c-b5ed-b02af3bd93ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204713(v=OCS.15)
ms:contentKeyID: 49306014
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resolução de problemas no Plug-in Lync VDI no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-10_

## Solucionando problemas com a instalação do plug-in VDI do Lync em um cliente fino

Caso existam problemas com a instalação de um plug-in VDI em um cliente fino, verifique o seguinte:

  - Assegure-se de que há espaço em disco suficiente na pasta que você especificou nas variáveis do sistema TEMP e TMP.

  - Assegure-se de que a proteção contra gravação está desligada. Consulte a documentação do fabricante do seu dispositivo para instruções.

## Solucionando problemas com pareamento

Quando o pareamento do plug-in VDI falha, o ícone de pareamento no canto inferior direito é exibido como um "X" vermelho, como mostrado a seguir:

![Ícone VDI do Lync que mostra o emparelhamento bem-sucedido](images/JJ204948.303d618c-4bc8-41c4-8553-2475de0d395e(OCS.15).png "Ícone VDI do Lync que mostra o emparelhamento bem-sucedido")

A seguir estão possíveis razões para falhas e as ações corretivas que você pode tomar.

  - **O usuário inseriu credenciais incorretas durante a entrada.**
    
    O usuário deve sair do Lync e entrar novamente com as credenciais corretas. A caixa de diálogo de pareamento reaparecerá e mostrará se o pareamento teve êxito.

  - **Outra instância do cliente de área de trabalho remota está sendo executada.**
    
    Caso estejam usando Conexão de Área de Trabalho Remota no Windows, os usuários devem fazer o seguinte:
    
    1.  Iniciar o Gerenciador de Tarefas: pressionar **Alt+Ctrl+Delete**, e então clicar em **Iniciar Gerenciador de Tarefas**.
    
    2.  Clique na guia **Processos** e procure por todos os processos chamados **mstsc.exe** na lista.
    
    3.  Selecione cada processo **mstsc.exe** e então clique em **Finalizar Processo**.
    
    4.  Inicie uma nova sessão de área de trabalho remota e tente conectar novamente.

  - **Os arquivos necessários não foram instalados corretamente.**
    
    Depois que o plug-in tenha sido instalado no computador local, os arquivos a seguir devem estar presentes em C:\\Program Files\\Microsoft Office\\Office15 (ou a letra de unidade apropriada):
    
      - LyncVdiPlugin.dll
    
      - UcVdi.dll
    
    Caso existam quaisquer problemas com o pareamento VDI, verifique para se assegurar que estes arquivos estão presentes no computador local.

  - **O cliente do Lync está sendo executado no computador local.**
    
    Para usar o plug-in VDI do Lync, um cliente do Lync não pode estar sendo executado no computador local, do contrário o pareamento falhará. Como prática recomendada, o usuário não deve instalar um cliente do Lync no computador local.

