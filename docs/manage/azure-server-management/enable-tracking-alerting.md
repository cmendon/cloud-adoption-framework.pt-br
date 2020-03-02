---
title: Habilitar acompanhamento e alertas para alterações críticas
description: Habilitar acompanhamento e alertas para alterações críticas
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 4581c865f3dd928df91e7e1eef97a0ea341e4ccb
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223500"
---
# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Habilitar acompanhamento e alertas para alterações críticas

O Azure Controle de Alterações e o inventário fornecem alertas sobre o estado de configuração do ambiente híbrido e alterações nesse ambiente. Ele pode relatar alterações críticas de arquivo, serviço, software e registro que podem afetar os servidores implantados.

Por padrão, o serviço de inventário de automação do Azure não monitora arquivos ou configurações do registro. A solução fornece uma lista de chaves do registro que recomendamos para o monitoramento. Para ver essa lista, acesse sua conta de automação na portal do Azure e, em seguida, selecione **inventário** > **Editar configurações**.

![Captura de tela da exibição de inventário da automação do Azure no portal do Azure](./media/change-tracking1.png)

Para obter mais informações sobre cada chave do registro, consulte [controle de alterações da chave do registro](https://docs.microsoft.com/azure/automation/automation-change-tracking#registry-key-change-tracking). Selecione qualquer chave a ser avaliada e, em seguida, habilite-a. A configuração é aplicada a todas as VMs habilitadas no espaço de trabalho atual.

Você também pode usar o serviço para controlar alterações de arquivo críticas. Por exemplo, talvez você queira acompanhar o arquivo C:\Windows\System32\drivers\etc\hosts porque o sistema operacional o utiliza para mapear nomes de host para endereços IP. As alterações nesse arquivo podem causar problemas de conectividade ou redirecionar o tráfego para sites perigosos.

Para habilitar o rastreamento de conteúdo de arquivo para o arquivo de hosts, siga as etapas em [Habilitar rastreamento de conteúdo de arquivo](https://docs.microsoft.com/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

Você também pode adicionar um alerta para alterações nos arquivos que está acompanhando. Por exemplo, digamos que você deseja definir um alerta para alterações no arquivo de hosts. Selecione **log Analytics** na barra de comandos ou na pesquisa de logs para o espaço de trabalho log Analytics vinculado. Em Log Analytics, use a consulta a seguir para procurar alterações no arquivo de hosts:

```kusto
ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
```

![Captura de tela da Log Analytics editor de consultas no portal do Azure](./media/change-tracking2.png)

Essa consulta pesquisa alterações no conteúdo de arquivos que têm um caminho que contém a palavra "hosts". Você também pode procurar um arquivo específico alterando o parâmetro Path. (Por exemplo, `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`.)
  
Depois que a consulta retornar os resultados, selecione **nova regra de alerta** para abrir o editor de regra de alerta. Você também pode acessar esse editor por meio de Azure Monitor no portal do Azure.

No editor de regras de alerta, examine a consulta e altere a lógica de alerta, se necessário. Nesse caso, queremos que o alerta seja gerado se alguma alteração for detectada em qualquer computador no ambiente.

![Captura de tela do editor de regras de alerta Log Analytics no portal do Azure](./media/change-tracking3.png)

Depois de definir a lógica da condição, você pode atribuir grupos de ações para executar ações em resposta ao alerta. Neste exemplo, quando o alerta é gerado, os emails são enviados e um tíquete de ITSM é criado. Você pode executar muitas outras ações úteis, como disparar uma função do Azure, um runbook de automação do Azure, um webhook ou um aplicativo lógico.

![Captura de tela do resumo da regra de alerta de exemplo no portal do Azure](./media/change-tracking4.png)

Depois de definir todos os parâmetros e a lógica, aplique o alerta ao ambiente.

## <a name="tracking-and-alerting-examples"></a>Exemplos de acompanhamento e alertas

Esta seção mostra outros cenários comuns para acompanhamento e alertas que talvez você queira usar.

### <a name="driver-file-changed"></a>Arquivo de driver alterado

Use a consulta a seguir para detectar se os arquivos de driver são alterados, adicionados ou removidos. É útil para controlar alterações em arquivos de sistema críticos.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Serviço específico interrompido

Use a consulta a seguir para controlar as alterações nos serviços críticos do sistema.

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Novo software instalado

Use a consulta a seguir para ambientes que precisam bloquear as configurações de software.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>A versão específica do software é ou não está instalada em um computador

Use a consulta a seguir para avaliar a segurança. Essa consulta faz referência a `ConfigurationData`, que contém os logs de inventário e fornece o estado de configuração da última reportada, não as alterações.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-the-registry"></a>DLL conhecida alterada por meio do registro

Use a consulta a seguir para detectar alterações em chaves de registro conhecidas.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Próximas etapas

Saiba como usar a automação do Azure para [criar agendas de atualização](./update-schedules.md) para gerenciar atualizações em seus servidores.

> [!div class="nextstepaction"]
> [Criar agendas de atualização](./update-schedules.md)
