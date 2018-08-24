---
title: 'Lync Server 2013: Definindo a política de local'
TOCTitle: Definindo a política de local
ms:assetid: da3cca7f-f6e5-4b6f-90a1-2008e3dd1ebd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398962(v=OCS.15)
ms:contentKeyID: 49308293
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo a política de local para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

Cada política de local contém as seguintes informações:

  - **Serviços de emergência habilitados**  
    Quando este valor é **Sim**, o cliente é habilitado para E9-1-1. Quando um cliente registrar, tenta adquirir um local do Serviço de Informações de Local e incluirá a informação de local como parte de uma chamada de emergência.

<!-- end list -->

  - **Local necessário**  
    Esta configuração é usada somente quando **Serviços de Emergência Habilitados** estiver definido como **Sim**.
    
    É possível definir a configuração **Local Necessário** para definir o comportamento do cliente. A definição do valor como **Não** significa que o usuário não receberá uma solicitação de local. A definição do valor como **Sim** significa que o usuário receberá uma solicitação por um local, mas poderá ignorar a solicitação. A definição do valor como **Aviso de isenção de responsabilidade** significa que o usuário receberá uma solicitação por um local e mostrará um aviso de isenção de responsabilidade caso ele tente ignorar a solicitação. Em todos os casos, o usuário pode continuar a usar o cliente.
    
    > [!NOTE]  
    > O texto do aviso de isenção de responsabilidade não aparecerá se um usuário inserir manualmente um local antes de ser habilitado para E9-1-1. As atualizações para o texto do aviso de isenção de responsabilidade não será visualizado pelos usuários que já visualizaram o aviso de isenção de responsabilidade.

<!-- end list -->

  - **Isenção de Responsabilidade do Serviço de Emergência Avançado**  
    Esta configuração especifica o aviso de isenção que o usuário ver se ignorar o aviso em um local. No Lync Server 2013, é possível usar a política de local para definir aviso de isenção para diferentes locais ou diferentes conjuntos de usuários.
    
    > [!NOTE]  
    > Esta configuração de política de local difere do Lync Server 2010, onde você usou o cmdlet <strong>Set-CsEnhancedEmergencyServiceDisclaimer</strong> para definir um aviso de isenção global para toda a organização. Se um aviso de isenção global já existir, você precisa especificar o aviso de isenção na política de local. Isto é, Lync Server 2013 usa apenas o aviso de isenção especificado na política de local.

<!-- end list -->

  - **Sequência de discagem de emergência**  
    Esta sequência de discagem (menos o “+” inicial, mas incluindo qualquer normalização realizada pelo Plano de discagem do usuário do Lync) que significa que uma chamada é uma chamada de emergência. A **Sequência de discagem de emergência** faz com que o cliente inclua na chamada informações sobre o local e sobre retorno de chamada.
    
    > [!NOTE]  
    > Se sua organização não usa um prefixo de acesso de linha externa, não será necessário criar uma regra de normalização do Plano de discagem correspondente que acrescenta um “+” à sequência 911 antes de enviar a chamada ao Roteamento de saída em um servidor de pool do Lync; o “+” será automaticamente pré-demarcado pelo cliente do Lync como resultado da política de local. No entanto, se seu site usar um prefixo de acesso externo, é necessário adicionar uma regra de normalização à política de Plano de discagem aplicável que retira o prefixo de acesso externo e adiciona o “+”. Por exemplo, se seu local usa um prefixo de acesso externo de 9 e um usuário discar 9 911 para fazer uma chamada de emergência, o cliente usará sua política de Plano de discagem para normalizar isso para +911 antes de ser avaliado pelas rotas no perfil de local do chamador.

<!-- end list -->

  - **Máscaras da sequência de discagem de emergência**  
    Uma lista separada por ponto e vírgula de sequências de discagem a serem traduzidas para a **Sequência de discagem de emergência**. Por exemplo, você pode querer adicionar 112, que é o número do serviço de emergência em grande parte da Europa. Talvez um usuário do Lync vindo da Europa não saiba que 911 é o número de emergência nos EUA, mas ele pode discar 112 e obter o mesmo resultado. Assim como ocorre com a Sequência de discagem de emergência, não inclua um “+” antes de cada número e se você usar os códigos de acesso de linha externa, certifique-se de que existam regras de normalização na política de Plano de discagem do usuário para retirar o dígito do código de acesso.

<!-- end list -->

  - **Uso de PSTN**  
    O nome do Uso de PSTN que contém os caminhos de roteamento que determinam para qual tronco SIP, gateway PSTN ou gateway ELIN as chamadas serão encaminhadas.
    
    > [!NOTE]  
    > É possível atribuir apenas um Uso a uma política de local. Esse Uso de PSTN substitui os Usos de PSTN atribuídos à política de voz do usuário, mas se aplica somente às chamadas feitas para a Sequência de discagem de emergência ou uma das Máscaras de sequência de chamada de emergência.

<!-- end list -->

  - **URI de notificação**  
    Especifica um ou mais URIs SIP do pessoal de segurança que receberá uma notificação de mensagem instantânea (IM) quando uma chamada de emergência for realizada. Os grupos de distribuição são suportados.

<!-- end list -->

  - **URI de conferência**  
    Especifica um número DID (discagem direta interna) (normalmente um número do suporte de segurança) que deve ser verificado quando uma chamada de emergência é feita.

<!-- end list -->

  - **Modo de conferência**  
    Especifica se o URI de conferência será inserido na chamada de emergência usando comunicação de uma ou duas vias.

<!-- end list -->

  - **Intervalo de atualização de local**  
    Especifica a quantidade de tempo (em horas) entre as solicitações do cliente para uma atualização de local do Serviço de Informações de Local. O valor pode ser definido para qualquer valor entre 1 e 12. O valor padrão é 4.

