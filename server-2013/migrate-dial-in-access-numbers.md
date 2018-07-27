---
title: Migrar números de acesso de discagem
TOCTitle: Migrar números de acesso de discagem
ms:assetid: e0dfaed2-64c7-45cb-aaa9-d6117a26625d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721909(v=OCS.15)
ms:contentKeyID: 49886440
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar números de acesso de discagem

 

_**Tópico modificado em:** 2012-10-19_

Migrando números de acesso discado do Lync Server 2010 para o Lync Server 2013 exige a execução do cmdlet **Move-CsApplicationEndpoint** para migrar os objetos de contato. Durante o período de coexistência entre o Lync Server 2010 e Lync Server 2013, os números de acesso discados criados no Lync Server 2013 se comportam da mesma forma que os números de acesso discados criados no Lync Server 2010, conforme descrito nesta seção.

Números de acesso discado criados no Lync Server 2010, mas movidos para o Lync Server 2013 ou criados no Lync Server 2013 antes, durante ou após a migração possuem as seguintes características:

  - Não aparecem nos convites de reunião do Office Communications Server 2007 R2 e na página de número de acesso de discagem.

  - Aparecem nos convites de reunião do Lync Server 2010 e na página de número de acesso de discagem.

  - Aparecem nos convites de reunião do Lync Server 2013 e na página de número de acesso de discagem.

  - Não pode ser exibido ou modificado na ferramenta administrativa do Office Communications Server 2007 R2.

  - Pode ser exibido e modificado no Painel de Controle do Lync Server 2010 e no Shell de Gerenciamento do Lync Server 2010.

  - Pode ser exibido e modificado no Painel de Controle do Lync Server 2013 e no Shell de Gerenciamento do Lync Server 2013.

  - Podem ser sequenciado novamente com a região usando o cmdlet Set-CsDialinConferencingAccessNumber com o parâmetro Priority.

É necessário concluir a migração dos números de acesso de discagem que apontam para um pool do Lync Server 2010 antes de encerrar o pool do Lync Server 2010. Se você não concluir a migração do número de acesso de discagem conforme descrito no procedimento a seguir, as chamadas recebidas para os números de acesso falharão.

> [!IMPORTANT]  
> É necessário realizar esse procedimento antes de encerrar o pool do Lync Server 2010.

> [!NOTE]  
> Recomendamos que você mova os números de acesso de discagem quando o uso da rede estiver baixo, caso exista um período curto de interrupção do serviço.

**Para identificar e mover os números de acesso de discagem**

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Para mover cada número de acesso de discagem para um pool hospedado no Lync Server 2013, na linha de comando, execute:
    
        Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>

3.  Abrir o Painel de Controle do Lync Server.

4.  Na barra de navegação esquerda, clique em **Conferência**.

5.  Clique na guia **Número de Acesso Discado**.

6.  Verifique se nenhum número de acesso discado permanece para o pool do Lync Server 2010 que você está migrando.
    
    > [!NOTE]  
    > Quando todos os números de acesso de discagem apontarem para o pool do Lync Server 2013, você poderá encerrar o pool do Lync Server 2010.

**Verificar a migração do número de acesso discado usando o Painel de Controle do Lync Server**

1.  De uma conta de usuário atribuída para a função **CsUserAdministrator** ou a função **CsAdministrator**, faça o login em qualquer computador na sua implantação interna.

2.  Abrir o Painel de Controle do Lync Server.

3.  Na barra de navegação esquerda, clique em **Conferência**.

4.  Clique na guia **Número de Acesso Discado**.

5.  Verifique se todos os números de acesso discados foram migrados para o pool hospedado no Lync Server 2013.

**Verifique a migração do número de acesso discado usando o Shell de Gerenciamento do Lync Server**

1.  Abrir o Shell de Gerenciamento do Lync Server.

2.  Para retornar todos os números de acesso de conferência discada migrados, na linha de comando, execute:
    
        Get-CsDialInConferencingAccessNumber -Filter {Pool -eq "<FQDN of the pool to which the access number is moved>"}

3.  Verifique se todos os números de acesso discado foram migrados para o pool hospedado no Lync Server 2013.

