---
title: Mesclar usando o assistente de Mesclagem do Construtor de Topologia
TOCTitle: Mesclar usando o assistente de Mesclagem do Construtor de Topologia
ms:assetid: c3f3c425-dab6-4dcd-bf0e-d7fde05f2ebf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205243(v=OCS.15)
ms:contentKeyID: 49308028
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mesclar usando o assistente de Mesclagem do Construtor de Topologia

 

_**Tópico modificado em:** 2012-10-02_

1.  Baixar a implantação existente utilizando o Construtor de Topologia.

2.  No menu **Ação**, selecione **Mesclar o Office Communications Server 2007 R2**.

3.  Clique em **Avançar**.

4.  Em **Especificar Configuração de Borda**, clique em **Adicionar**.
    
    ![Assistente para Mesclar Topologia, página Especificar a Configuração de Borda](images/JJ205243.cdca609d-d4d5-47d9-9ff8-8b1daa4106e1(OCS.15).jpg "Assistente para Mesclar Topologia, página Especificar a Configuração de Borda")  

5.  Em **Especificar Versão de Borda**, insira o tipo de configuração do Servidor de Borda e clique em **Avançar**. Esse exemplo usa a opção **Servidor de Borda Único**.
    
    > [!IMPORTANT]  
    > <strong>Implantação de Borda Expandida</strong> não é uma configuração suportada. Um <strong>Servidor de Borda Expandida</strong> deve primeiro ser convertido em um <strong>Servidor de Borda Único</strong> ou em um Servidor <strong>Implantação de Borda Consolidada Balanceada</strong>.

6.  Em **Especificar Configurações de Borda Interna**, insira as informações relevantes para FQDN e portas internos do pool da Borda conforme necessário e clique em **Avançar**.
    
    ![Caixa de diálogo Especificar Configurações de Borda Interna](images/JJ205243.dd664761-839c-4ac8-bd1a-5525589dfbb0(OCS.15).jpg "Caixa de diálogo Especificar Configurações de Borda Interna")  

7.  Em **Especificar Borda Externa**, insira as informações de FQDN de conferência da Web do seu Servidor de Borda.
    
    > [!IMPORTANT]  
    > Antes de clicar em <strong>Avançar</strong>, realize a próxima etapa deste procedimento. É muito importante que você não pule esta etapa.

8.  Marque a caixa de seleção **Este pool de Borda é usado para conectividade de IM pública e de federação** se você planeja usar esse Servidor de Borda do Office Communications Server 2007 R2 herdado para federação. Se você possui vários Servidores de Borda implantados, somente um deles ficará habilitado para federação. Se você não marcar essa caixa e depois decidir que quer habilitar a federação, deve executar o assistente de Mesclagem de Construtor de Topologia novamente e depois publicar sua topologia novamente.
    
    ![Caixa de diálogo Servidor de Borda, página Especificar Borda Externa](images/JJ205243.32e97ce5-92f0-477e-8125-5d2ece237b13(OCS.15).jpg "Caixa de diálogo Servidor de Borda, página Especificar Borda Externa")  

9.  Em **Especificar próximo salto**, insira o FQDN do próximo salto em seu ambiente. Clique em **Finalizar**.
    
    ![Caixa de diálogo Servidor de Borda, página Especificar Próximo Salto](images/JJ205243.e734ee0d-f91c-4f3f-8ae6-248ecabcf678(OCS.15).jpg "Caixa de diálogo Servidor de Borda, página Especificar Próximo Salto")  

10. Em **Especificar a Configuração de Borda**, se todos os seus Servidores de Borda do Office Communications Server 2007 R2 tiverem sido adicionados, clique em **Avançar**. Se você tiver mais Servidores de Borda do Office Communications Server 2007 R2 para adicionar, repita este procedimento iniciando na etapa 4.

11. Em **Especificar porta SIP interna**, selecione a configuração padrão (isto é, se você não modificou a porta SIP padrão). Faça as alterações conforme seja apropriado se você não estiver usando uma porta padrão de 5061 e clique em **Avançar**.

12. Em **Resumo**, clique em **Avançar** para começar a mesclar as topologias.

13. A página do assistente verifica se a mesclagem das topologias foi bem-sucedida.

14. Na coluna **Status**, verifique se o valor é **Êxito** e clique em **Finalizar**.

15. No painel esquerdo do Construtor de Topologia, você deve ver agora o **BackCompatSite**, que indica que seu ambiente do Office Communications Server 2007 R2 foi mesclado com o Lync Server 2013.
    
    ![Construtor de Topologias mostrando uma topologia mesclada](images/JJ205243.62751c76-f018-4c6d-bb48-c61ef8974d31(OCS.15).jpg "Construtor de Topologias mostrando uma topologia mesclada")  

16. No painel **Ações**, no menu **Publicar topologia** e em **Avançar**.

17. Quando o **Assistente de publicação** for concluído, clique em **Finalizar**.
    
    > [!NOTE]  
    > É importante que você complete o próximo tópico, <a href="import-policies-and-settings.md">Importar políticas e configurações</a>, para garantir que as configurações da política herdada foram importadas ao Lync Server 2013.
