---
title: 'Lync Server 2013: Entrando e usando o Lync 2013 na máquina virtual'
TOCTitle: Entrando e usando o Lync 2013 na máquina virtual
ms:assetid: 6140fc19-5bef-4b58-9b0f-19112b5ecd00
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204948(v=OCS.15)
ms:contentKeyID: 49306880
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Entrando e usando o Lync 2013 na máquina virtual

 

_**Tópico modificado em:** 2012-10-03_

Depois que o plug-in de VDI for habilitado, as etapas a seguir ocorrerão quando o usuário entrar no Lync 2013.

1.  O usuário digita suas credenciais no cliente do Lync 2013 em execução na máquina virtual.

2.  Depois que o Lync detecta a disponibilidade do plug-in de VDI, o Lync solicita que o usuário insira novamente suas credenciais. Nessa caixa de diálogo, é recomendável que o usuário marque a caixa de seleção **Salvar minha senha** para que não precise inserir as credenciais na próxima entrada.

3.  O Lync começará a ser emparelhado ao plug-in de VDI. Antes da conclusão do emparelhamento, o cliente exibirá dois ícones na barra de status do Lync. O ícone no canto inferior esquerdo indica que nenhum dispositivo de áudio está disponível, e o ícone piscante no canto inferior direito indica que o emparelhamento de VDI está em andamento:
    
    ![Ícone VDI do Lync que mostra o emparelhamento bem-sucedido](images/JJ204948.303d618c-4bc8-41c4-8553-2475de0d395e(OCS.15).png "Ícone VDI do Lync que mostra o emparelhamento bem-sucedido")  

4.  Após o emparelhamento bem-sucedido de VDI, os ícones mudarão para indicar o dispositivo de áudio que será usado para chamadas e o êxito do emparelhamento de VDI:
    
    ![Ícone de emparelhamento VDI do Lync que mostra êxito](images/JJ204948.57be3387-a3e5-4949-831e-f5ff9fcc5598(OCS.15).png "Ícone de emparelhamento VDI do Lync que mostra êxito")  

5.  Depois que o Lync for emparelhado com o plug-in de VDI, o usuário poderá ver sua presença em dispositivos compatíveis com o Lync que estiverem conectados ao computador local. Agora, o usuário poderá realizar e atender chamadas como de costume.

