---
title: Ferramenta de diagnósticos do Lync PreCall no Lync Server 2013
TOCTitle: Ferramenta de diagnósticos do Lync PreCall no Lync Server 2013
ms:assetid: 0ff291ec-cfb4-43eb-b5d6-a7a325681e3f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn451255(v=OCS.15)
ms:contentKeyID: 59602785
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ferramenta de diagnósticos do Lync PreCall no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O PCD (PreCall Diagnostics Tool) do Lync é um aplicativo baseado em cliente que permite a você ver como o estado atual da sua rede poderia afetar a qualidade do áudio em uma futura chamada do Enterprise Voice.

O PCD é mais útil em situações onde o último salto de uma rede provavelmente será o mais fraco (por exemplo, com laptops em uma rede Wi-Fi pública ou usuários residenciais). O PCD cria um pequeno fluxo de pacotes que atravessa esse trecho final da rede. A ferramenta então analisa o fluxo de pacotes para estimar como o jitter e a perda neste trecho poderia afetar a qualidade da chamada e então fornece um relatório. Você pode executar o PCD continuamente no cliente, mesmo enquanto as chamadas estiverem sendo feitas. O fluxo de pacotes não tem um efeito significativo na largura de banda.

**A versão mais recente do PCD, versão 1.1, inclui os seguintes aperfeiçoamentos:**

  - Suporte para senhas mais longas, que agora podem ter até 127 caracteres

  - Diagnóstico adicional para problemas de entrada de autenticação

  - Melhor suporte para implantações híbridas do Lync

  - Atualizações do seletor de credencial

  - Melhorias na estabilidade

Gostaríamos de receber comentários. Envie todas as dúvidas ou problemas de suporte para o alias [Comentários sobre o PCD](mailto:pcdfb@microsoft.com) em <pcdfb@microsoft.com>.

Este tópico inclui as seguintes seções:

  - Versões do PCD do Lync

  - Requisitos do sistema do PCD do Lync

  - Recursos do PCD do Lync

  - Executando o PCD do Lync

  - Desinstalando o PCD do Lync

## Versões do PCD do Lync

Este tópico descreve as versões a seguir da ferramenta, disponíveis para download gratuito:

  - Windows Desktop App ([http://go.microsoft.com/fwlink/?LinkId=327914](http://go.microsoft.com/fwlink/p/?linkid=327914))

  - Windows 8 Modern App ([http://go.microsoft.com/fwlink/?LinkId=322110](http://go.microsoft.com/fwlink/p/?linkid=322110))

> [!NOTE]  
> Os usuários do Office 365 Lync podem usar ambas as versões do PCD.

Se quiser usar uma versão anterior do PCD, consulte o seguinte:

  - A versão de 32 bits do PCD está disponível como download gratuito do Centro de Download da Microsoft em [Office Communications Server 2007 R2, Ferramenta do Resource Kit de PreCallDiagnostic (32 bits)](http://go.microsoft.com/fwlink/p/?linkid=164769).

  - A versão de 64 bits do PCD foi incluída nas Ferramentas do Resource Kit do Office Communications Server 2007 R2, que estão disponíveis como download gratuito no Centro de Download da Microsoft em [Ferramentas do Resource Kit do Office Communications Server 2007 R2](http://go.microsoft.com/fwlink/p/?linkid=145159).

## Requisitos do sistema do PCD do Lync

> [!NOTE]  
> O PCD exige que a API da Web das Comunicações Unificadas (UCWA) esteja instalada e configurada para dar suporte a clientes móveis na implantação do Lync Server. O UCWA é instalado com o Lync Server.

## Requisitos do Aplicativo da Área de Trabalho do Windows

  - Qualquer edição do sistema operacional Windows 7 ou Windows 8

  - O Microsoft .NET Framework 4.5 está disponível em [http://go.microsoft.com/fwlink/?LinkId=327790](http://go.microsoft.com/fwlink/p/?linkid=327790)

## Requisitos do Windows 8 Modern App

  - Qualquer edição do sistema operacional Windows 8

  - O Microsoft .NET Framework 4.5 está disponível em [http://go.microsoft.com/fwlink/?LinkId=327790](http://go.microsoft.com/fwlink/p/?linkid=327790)

## Recursos do PCD do Lync

O PCD do Lync inclui os seguintes recursos:

  - Executar no padrão Sob Demanda (intermitências de 2 minutos)

  - Executar no modo Sempre Ativado (até 24 horas no modo de exibição ajustado)

  - Modo de exibição histórico de suas execuções de teste

  - Diagnosticar falhas de entrada (Somente PCD do Lync para Windows 8)

![Captura de tela do andamento da entrada dos recursos de PCD do Lync](images/Dn451255.7e0eb891-1481-47ae-8d63-164468f69c96(OCS.15).png "Captura de tela do andamento da entrada dos recursos de PCD do Lync")

  - Exibição gráfica de métricas de rede – MOS de rede, Perda de Pacotes e Jitter Interchegadas em tela cheia e modo de exibição ajustado.

**Modo de exibição de tela cheia**

![Gráficos de resultados de teste da PreCall Diagnostic Tool](images/Dn451255.5d01fd94-9e59-4823-96c7-7a1c83dd7d31(OCS.15).png "Gráficos de resultados de teste da PreCall Diagnostic Tool")

**Modo de exibição ajustado**

![Resultados do teste de Utilização da PreCall Diagnostic Tool](images/Dn451255.30501ba7-22d1-4db1-9297-56cf7dc6721c(OCS.15).png "Resultados do teste de Utilização da PreCall Diagnostic Tool")

## Executando o PCD do Lync

## Executando o Aplicativo da Área de Trabalho do Windows

1.  Para iniciar o PCD em um sistema Windows 7, selecione **PreCall Diagnostics** no menu **Iniciar**.
    
    Para iniciar o PCD em um sistema Windows 8, selecione o ícone em sua tela Inicial ou pesquise “PreCall Diagnostics.”
    
    ![Ícone da ferramenta PreCall Diagnostic](images/Dn451255.c9800fde-54f6-4efe-bb35-1a38064ec380(OCS.15).png "Ícone da ferramenta PreCall Diagnostic")

2.  Quando a ferramenta for iniciada, selecione seu método preferencial de fornecer credenciais e selecionar o modo operacional de rede na caixa de diálogo **Opções da Ferramenta PreCall Diagnostics**, então selecione **OK**:

3.  Selecione o botão **Iniciar Teste** para iniciar a execução do diagnóstico.
    
    Se você tiver selecionado a opção **Usar credenciais de rede**, o teste será iniciado imediatamente.
    
    Se você selecionou a opção **Deixe-me inserir minhas credenciais**, a caixa de diálogo **Segurança do Windows** será aberta. Depois de inserir suas credenciais, o teste será iniciado.

## Executando o Windows 8 Modern App


1.  Para iniciar o PCD, selecione o ícone em sua tela Inicial ou pesquise “PreCall Diagnostics.”
    
    ![Ícone da ferramenta PreCall Diagnostic](images/Dn451255.c9800fde-54f6-4efe-bb35-1a38064ec380(OCS.15).png "Ícone da ferramenta PreCall Diagnostic")

2.  Quando a ferramenta for iniciada, forneça suas credenciais do Lync e então selecione **OK**.
    
    ![Entrada na Lync PreCall Diagnostics Tool](images/Dn451255.88039914-4c68-48f6-a9fa-58cb4e3f3488(OCS.15).jpg "Entrada na Lync PreCall Diagnostics Tool")

3.  Selecione o botão **Iniciar teste** para iniciar a execução do diagnóstico.

## Desinstalando o PCD do Lync

Para remover o PCD do Lync, siga o procedimento para o seu sistema operacional:

  - Em um sistema Windows 7, abra o **Painel de Controle**, selecione **Programas e Recursos** e clique duas vezes em **Lync 2013 PreCall Diagnostics**.

  - Em um sistema Windows 8, clique com o botão direito no título do PCD e clique em **Desinstalar** na barra de aplicativos na parte inferior da tela inicial.

