---
title: Habilitar acompanhamento e alertas para alterações críticas
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Habilitar acompanhamento e alertas para alterações críticas
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 32f0a5f9b5d0fabe9e1989e54293b74aeb130b96
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565426"
---
# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Habilitar acompanhamento e alertas para alterações críticas

O Azure Controle de Alterações e o inventário fornecem alertas sobre o estado de configuração do ambiente híbrido e sobre quaisquer alterações no ambiente. Você pode monitorar as alterações de arquivo crítico, de serviço, de software e de registro que podem afetar os servidores implantados.

Por padrão, o serviço de inventário de automação do Azure não monitora arquivos ou configurações do registro. A solução fornece uma lista de chaves do registro que recomendamos para o monitoramento. Para ver essa lista, acesse sua conta de automação no portal do Azure e selecione **inventário** > **Editar configurações**.

![Captura de tela da exibição de inventário da automação do Azure no portal do Azure](./media/change-tracking1.png)

Para obter mais informações sobre cada chave do registro, consulte [controle de alterações da chave do registro](https://docs.microsoft.com/azure/automation/automation-change-tracking#registry-key-change-tracking). Você pode avaliar e, em seguida, habilitar cada chave selecionando-a. A configuração é aplicada a todas as VMs habilitadas no espaço de trabalho atual.

Você também pode controlar alterações de arquivo críticas. Por exemplo, talvez você queira acompanhar o arquivo C:\Windows\System32\drivers\etc\hosts porque o sistema operacional o utiliza para mapear nomes de host para endereços IP. Qualquer alteração nesse arquivo pode causar problemas de conectividade ou redirecionar o tráfego para sites perigosos.

Para habilitar o rastreamento de conteúdo de arquivo para o arquivo de hosts, siga as etapas em [Habilitar rastreamento de conteúdo de arquivo](https://docs.microsoft.com/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

Você também pode adicionar um alerta para alterações feitas nos arquivos que está acompanhando. Por exemplo, digamos que você deseja definir um alerta para as alterações feitas no arquivo de hosts. Comece acessando Log Analytics selecionando **log Analytics** na barra de comandos ou abrindo a pesquisa de logs para o espaço de trabalho log Analytics vinculado. Depois que estiver em Log Analytics, procure alterações de conteúdo no arquivo de hosts usando a seguinte consulta:

```kusto
ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
```

![Captura de tela da Log Analytics editor de consultas no portal do Azure](./media/change-tracking2.png)

Essa consulta pesquisa alterações no conteúdo de arquivos que têm um caminho que contém a palavra "hosts". Você também pode procurar um arquivo específico alterando o parâmetro Path. (Por exemplo, `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`.)
  
Depois que a consulta retornar os resultados, selecione **nova regra de alerta** para abrir o editor de regras de alerta. Você também pode acessar esse editor por meio de Azure Monitor no portal do Azure.

No editor de regras de alerta, examine a consulta e altere a lógica de alerta, se necessário. Nesse caso, queremos que o alerta seja gerado se alguma alteração for detectada em qualquer computador no ambiente.

![Captura de tela do editor de regras de alerta Log Analytics no portal do Azure](./media/change-tracking3.png)

Depois de definir a lógica da condição, você pode atribuir grupos de ações para executar ações em resposta ao alerta. Neste exemplo, quando o alerta é gerado, os emails são enviados e um tíquete de ITSM é criado. Você pode executar muitas outras ações úteis, como disparar uma função do Azure, um runbook de automação do Azure, um webhook ou um aplicativo lógico.

![Captura de tela do resumo da regra de alerta de exemplo no portal do Azure](./media/change-tracking4.png)

Depois de definir todos os parâmetros e a lógica, aplique o alerta ao ambiente.

## <a name="more-tracking-and-alerting-examples"></a>Mais exemplos de acompanhamento e alertas

Aqui estão alguns outros cenários comuns para acompanhamento e alertas que você talvez queira considerar:

### <a name="driver-file-changed"></a>Arquivo de driver alterado

Detectar se os arquivos de driver são alterados, adicionados ou removidos. Útil para controlar alterações em arquivos de sistema críticos.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Serviço específico interrompido

Útil para controlar alterações em serviços críticos do sistema.

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Novo software instalado

Útil para ambientes que precisam bloquear configurações de software.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>A versão específica do software é ou não está instalada em um computador

Útil para avaliar a segurança. Observe que essa consulta faz referência a `ConfigurationData`, que contém os logs de inventário e relata o último estado de configuração relatado, não as alterações.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-registry"></a>DLL conhecida alterada por meio do registro

Útil para detectar alterações em chaves de registro bem conhecidas.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Próximas etapas

Saiba como gerenciar atualizações para seus servidores [criando agendas de atualização](./update-schedules.md) com a automação do Azure.

> [!div class="nextstepaction"]
> [Criar agendas de atualização](./update-schedules.md)
