---
title: Configurando o Windows 8 para cartões inteligentes virtuais
TOCTitle: Configurando o Windows 8 para cartões inteligentes virtuais
ms:assetid: 4916c167-4ee3-4f3e-b65c-33e588595112
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308564(v=OCS.15)
ms:contentKeyID: 56270386
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Windows 8 para cartões inteligentes virtuais

 

_**Tópico modificado em:** 2016-12-08_

Um fator que deve ser levado em consideração na implantação da autenticação de dois fatores e na tecnologia de cartão inteligente é o custo da implementação. O Windows 8 oferece vários novas capacidades de segurança, e um dos novos recursos mais interessantes é o suporte a cartões inteligentes virtuais.

Para computadores que contam com um chip Trusted Platform Module (TPM) compatível com a especificação da versão 1.2, as organizações podem agora se beneficiar do logon com cartões inteligentes sem fazer mais nenhum investimento em hardware. Para obter mais informações, consulte Uso de cartões inteligentes virtuais com o Windows 8 em [http://go.microsoft.com/fwlink/p/?LinkId=313365](http://go.microsoft.com/fwlink/p/?linkid=313365).

## Para configurar o Windows 8 para cartões inteligentes virtuais

1.  Faça o logon no computador com o Windows 8 usando as credenciais de um usuário habilitado no Lync.

2.  Na tela Iniciar do Windows 8, mova seu cursor para o canto inferior direito da tela.

3.  Selecione a opção **Pesquisar** e pesquise **Prompt de comando**.

4.  Clique com o botão direito do mouse em **Prompt de comando** e selecione **Executar como administrador**.

5.  Abra o Console de Gerenciamento do Trusted Platform Module (TPM) executando o seguinte comando:
    
        Tpm.msc

6.  No Console de Gerenciamento do TPM, confira se a versão do seu TPM é 1.2 ou superior.
    
    > [!NOTE]  
    > Caso surja uma caixa de diálogo com a mensagem de que não foi possível encontrar o Trust Platform Module (TPM) compatível, verifique se o computador tem um módulo TPM compatível e se ele está habilitado na BIOS do sistema.

7.  Feche o Console de Gerenciamento do TPM

8.  No prompt de comando, crie um novo cartão inteligente virtual usando o seguinte comando:
    
        TpmVscMgr create /name MyVSC /pin default /adminkey random /generate
    
    > [!NOTE]  
    > Para personalizar o valor do PIN ao criar o cartão inteligente virtual, use o prompt /pin.

9.  No prompt de comando, abre o Console de Gerenciamento do computador executando o seguinte comando:
    
        CompMgmt.msc

10. No Console de Gerenciamento do computador, selecione **Gerenciamento de Dispositivos**.

11. Expanda **Leitores de cartão inteligente**.

12. Verifique se o novo leitor de cartão inteligente virtual foi criado com êxito.

