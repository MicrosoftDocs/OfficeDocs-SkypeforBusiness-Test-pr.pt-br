---
title: 'Lync Server 2013: Criar um caso de teste de roteamento de voz'
TOCTitle: Criar um caso de teste de roteamento de voz
ms:assetid: 43a07a5b-2f20-462a-81e5-d628c18391e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425935(v=OCS.15)
ms:contentKeyID: 49306558
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um caso de teste de roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-07_

## Para criar um caso de teste

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento deVoz** e em **Testar Roteamento de Voz** .

4.  Na página **Testar Roteamento de Voz**, clique em **Novo** para criar um novo caso de teste.

5.  Em **Nome**, digite um nome exclusivo para o caso de teste.
    
    O nome deve ser exclusivo entre todos os casos de teste de roteamento voz na implantação do Enterprise Voice. Ele pode ter até 32 caracteres e pode conter qualquer caractere alfanumérico, além da barra invertida (\\), ponto (.) ou sublinhado (\_).

6.  Em **Número discado para fazer um teste**, digite o número discado que deseja usar para testar a configuração de roteamento que você especificar para esse caso de teste. Com base no plano de discagem, na rota e na política de voz, esse número será normalizado e exibido como saída.

7.  Na lista **Plano de Discagem**, selecione o plano de discagem a ser usado ao executar o teste. O padrão é o plano de discagem Global.

8.  Na lista **Política de Voz**, selecione a política de voz a ser usada ao executar o teste. O padrão é a política de voz Global.

9.  Em **Conversão esperada**, digite o número de telefone no formato que você espera ver após a conversão. Esse é o valor do número de telefone que você está testando depois que ele foi convertido pela primeira regra de normalização correspondente no plano de discagem selecionado. Quando você executa o caso de teste, se o número que está testando não resultar no valor em **Conversão esperada**, o teste falhará.

10. (Opcional) Na lista **Uso de PSTN esperado**, você pode selecionar o registro de uso da Rede Telefônica Pública Comutada (PSTN) que espera que seja usado ao executar o caso de teste, com base na política de voz e no plano de discagem especificado. Se um registro de uso diferente do PSTN for usado, o teste falhará.

11. (Opcional) Na lista **Rota esperada**, você pode selecionar a rota de voz que espera que seja usada ao executar o caso de teste, com base na política de voz e no plano de discagem especificado. Se um registro de uso diferente do PSTN for usado, o teste falhará.

12. (Opcional) Clique em **Executar** para executar o caso de teste. Os resultados são mostrados no painel à direita da página.

13. Clique em **OK**.

14. Clique em **Confirmar** e, em seguida, clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que criar um caso de teste de roteamento de voz, você deve executar o comando <strong>Confirmar tudo</strong> para publicar a alteração na configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.    
    Se o plano de discagem empregado no teste normaliza números de telefone que começam com um sinal de adição (por exemplo, +12065551219), esse plano pode causar a falha do teste de roteamento de voz. (O plano de discagem e a rota de voz funcionarão; de fato, Test-CsDialPlan será bem-sucedido. No entanto, o teste de roteamento de voz poderá falhar.) Isso deve ser considerado durante o teste de rotas de voz.

## Consulte Também

#### Tarefas

[Exportar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-export-voice-routing-test-cases.md)  
[Importar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-import-voice-routing-test-cases.md)  

#### Outros Recursos

[Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md)  
[Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

