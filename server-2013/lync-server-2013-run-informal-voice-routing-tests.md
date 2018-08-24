---
title: Executar testes de roteamento de voz informais no Lync Server 2013
TOCTitle: Executar testes de roteamento de voz informais no Lync Server 2013
ms:assetid: ea0e6059-bf04-4b03-b6d3-8f5534b731e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399049(v=OCS.15)
ms:contentKeyID: 49308487
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executar testes de roteamento de voz informais no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-07_

É possível usar a caixa de diálogo **Criar informações de caso de teste de roteamento de voz** para executar testes informais antes de criar um caso de teste real. Quando você estiver satisfeito com o resultado do teste, terá a opção de salvá-lo como um caso de teste formal.

## Para executar um teste de roteamento de voz informal

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de Voz** e então clique em **Testar Roteamento de Voz**.

4.  Na página **Testar Roteamento de Voz**, clique em **Criar informações do caso de teste de roteamento de voz**.

5.  No campo **Número discado**, digite o número de telefone que você deseja usar para este teste. Esse número será normalizado e exibido no campo **Número normalizado** do painel **Resultados**.

6.  Na lista **Plano de discagem**, selecione o plano de discagem a ser usado para testar o número discado. O padrão é o plano de discagem Padrão.
    
    Ao executar o teste, a primeira regra de normalização nesse plano de discagem que corresponde ao número discado será exibido no campo **Regra de normalização** do painel **Resultados**.

7.  Na lista **Política de Voz**, selecione a política de voz a ser usada para testar o número discado. O padrão é a política de voz Global.
    
    Ao executar o teste, o primeiro registro de uso de PSTN correspondente nessa política de voz será exibido no campo **Primeiro uso do PSTN** no painel **Resultados**. Além disso, a primeira rota de voz correspondente associada ao registro de uso desse PSTN será exibida no campo **Primeira rota**.

8.  (Opcional) Marque a caixa de seleção **Popular no usuário** se você quiser testar o número discado com base na política de voz atribuída a um usuário específico.
    
    1.  Clique em **Procurar** para exibir a caixa de seleção **Selecionar os Usuários do Enterprise Voice**.
    
    2.  Clique em **Localizar** para exibir a lista de usuários habilitados para o Enterprise Voice.
    
    3.  Clique duas vezes no nome do usuário cuja política de voz atribuída você deseja usar para este teste. O campo **Política** agora está preenchido com a política de voz atribuída ao usuário selecionado.
    
    Quando você executa o teste, o primeiro registro de uso de PSTN (Rede Telefônica Pública Comutada) correspondente nesta política de voz será exibido no campo **Primeiro uso do PSTN** do painel **Resultados**. Além disso, a primeira rota de voz correspondente associada ao registro de uso do PSTN será exibida no campo **Primeira rota**.

9.  Clique em **Executar** para executar o caso de teste. Os resultados são exibidos no painel direito da caixa de diálogo.

10. (Opcional) Clique em **Salvar como** se você quiser salvar esta configuração de teste como um caso de teste formal.
    
    1.  No campo **Nome** da caixa de diálogo **Salvar Informações do Caso de Teste de Roteamento de Voz**, digite um nome exclusivo para o caso de teste.
        
        O nome precisa ser exclusivo entre todos os casos de teste de roteamento de voz em sua implantação do Enterprise Voice. Ele pode conter até 32 caracteres e quaisquer caracteres alfanuméricos, além da barra invertida (\\), ponto (.) ou sublinhado (\_).
    
    2.  Observe que os campos restantes na caixa de diálogo **Salvar Informações do Caso de Teste de Roteamento** são somente leitura e são pré-preenchidos a partir dos resultados *e* configuração do teste informal. Verifique se essa é a configuração que você deseja salvar para o caso de teste.
        
        > [!NOTE]  
        > Os valores dos resultados do teste são usados para pré-preencher os campos na caixa de diálogo <strong>Salvar Informações do Caso de Teste de Roteamento de Voz</strong> da seguinte maneira:
        > <ul>        
        > <li><p><strong>Conversão esperada</strong> é pré-preenchida com o valor no campo <strong>Número normalizado</strong>.</p></li>  
        > 
        > <li><p><strong>Rota esperada</strong> é pré-preenchido com o valor no campo <strong>Primeira rota</strong>.</p></li>        
        > 
        > 
        > <li><p><strong>Registro esperado de uso do PSTN</strong> é pré-preenchido com o valor no campo <strong>Primeiro uso do PSTN</strong>.</p></li></ul>
        > Se nenhuma correspondência para qualquer um desses valores for encontrada durante a execução do teste, a entrada do campo correspondente ficará vazia na caixa de diálogo <strong>Salvar Informações do Caso de Teste de Roteamento de Voz</strong>.
    
    3.  Clique em **Ok** para salvar o caso de teste ou clique em **Cancelar** para voltar à caixa de diálogo **Exibir informações do caso de teste de roteamento de voz** para desenvolver ainda mais o teste antes de salvá-lo.

11. Clique em **Confirmar** e clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que você criar um caso de teste de roteamento de voz, deverá executar o comando <strong>Confirmar tudo</strong> para publicar o caso de teste. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação Operações.

## Consulte Também

#### Tarefas

[Criar um caso de teste de roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-routing-test-case.md)  
[Executar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-run-voice-routing-test-cases.md)  
[Exportar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-export-voice-routing-test-cases.md)  
[Importar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-import-voice-routing-test-cases.md)  

#### Outros Recursos

[Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md)  
[Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

