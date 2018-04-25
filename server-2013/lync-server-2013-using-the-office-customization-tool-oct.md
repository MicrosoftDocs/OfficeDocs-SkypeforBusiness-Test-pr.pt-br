---
title: Usando a Ferramenta de Personalização do Office (OCT)
TOCTitle: Usando a Ferramenta de Personalização do Office (OCT)
ms:assetid: 26647cb6-ba84-4ba7-8b6f-2cf86818e530
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204748(v=OCS.15)
ms:contentKeyID: 49306172
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando a Ferramenta de Personalização do Office (OCT)

 

_**Tópico modificado em:** 2016-12-08_

O Office Customization Tool (OCT) faz parte do programa de Instalação e é a ferramenta recomendada para várias personalizações. AO usar o OCT, você personaliza o Office e salva suas personalizações em um arquivo .msp de personalização de Instalação. Você coloca o arquivo na pasta Atualizações no ponto de instalação de rede. Ao instalar o Office, a Instalação procura por um arquivo de personalização da Instalação na pasta Atualizações e aplica as personalizações. A pasta Atualização pode ser usada apenas para implantar atualizações de software durante a instalação inicial do Office 2013.

O OCT faz parte da instalação e é incluído em versões de licença de volume do produto. Você executa o OCT digitando `setup.exe /admin` na linha de comando na raiz do ponto de instalação de rede que contém os arquivos de origem do Office 2013. Por exemplo, use o seguinte:

`\\server\share\Office15\setup.exe /admin`

Os administradores usam o OCT para criar um arquivo .msp de personalização da instalação. Como no OCT do Microsoft Office 2010, os administradores podem personalizar as seguintes áreas:

  - **Instalação** Usado para especificar o local de instalação padrão no nome da organização padrão e cliente, fontes de instalação de rede adicionais, chave do produto, contrato de licença do usuário final, nível de exibição, versões anteriores do Office para remover, programas personalizados para executar durante a instalação, configurações de segurança e propriedades de Instalação.

  - **Recursos** Usado para definir as configurações do usuário e personalizar como os recursos do Office são instalados. Os administradores podem usar o OCT para especificar os valores padrões iniciais das configurações do aplicativo do Office para usuários. Os usuários podem modificar a maioria das configurações após a instalação.

  - **Conteúdo adicional** Usado para adicionar ou remover arquivos, adicionar ou remover entradas do Registro e configurar atalhos.

  - **Outlook** Usado para personalizar o perfil padrão do Outlook do usuário, especificar as configurações do Exchange, adicionar contas, remover contas, exportar configurações e especificar grupos de Envio/Recebimento.

Para obter mais informações sobre o OCT, consulte [http://go.microsoft.com/fwlink/?linkid=267516\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267516%26clcid=0x416).

