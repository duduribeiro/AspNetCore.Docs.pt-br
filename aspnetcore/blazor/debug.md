---
title: Depurar ASP.NET Core mais incrivelmente
author: guardrex
description: Saiba como depurar aplicativos mais Incrivelmenteos.
monikerRange: '>= aspnetcore-3.0'
ms.author: riande
ms.custom: mvc
ms.date: 07/31/2019
uid: blazor/debug
ms.openlocfilehash: 37c6009727a4f62b61793adca0d83cdd53be4b9a
ms.sourcegitcommit: 3204bc89ae6354b61ee0a9b2770ebe5214b7790c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68948366"
---
# <a name="debug-aspnet-core-blazor"></a>Depurar ASP.NET Core mais incrivelmente

[Daniel Roth](https://github.com/danroth27)

Há suporte antecipado para depuração de aplicativos do lado do cliente mais recentes em execução no Webassembly no Chrome.

Os recursos do depurador são limitados. Os cenários disponíveis incluem:

* Definir e remover pontos de interrupção.
* Etapa única (`F10`) por meio da execução do código ou`F8`retomar ().
* Na exibição *locais* , observe os valores de qualquer variável local do tipo `int`, `string`e `bool`.
* Consulte a pilha de chamadas, incluindo cadeias de chamada que vão do JavaScript para o .NET e do .NET para o JavaScript.

Você *não pode*:

* Observe os valores de quaisquer locais que não sejam `int`um `string`, ou `bool`.
* Observe os valores de quaisquer propriedades ou campos de classe.
* Passe o mouse sobre variáveis para ver seus valores.
* Avalie as expressões no console.
* Passe pelas chamadas assíncronas.
* Execute a maioria dos outros cenários de depuração comuns.

O desenvolvimento de mais cenários de depuração é um foco contínuo da equipe de engenharia.

## <a name="prerequisites"></a>Pré-requisitos

A depuração requer um dos seguintes navegadores:

* Google Chrome (versão 70 ou posterior)
* Visualização do Microsoft Edge ([canal de desenvolvimento de borda](https://www.microsoftedgeinsider.com))

## <a name="procedure"></a>Procedimento

1. Execute um aplicativo do lado do cliente mais incrivelmente `Debug` na configuração. Passe a `--configuration Debug` opção para o comando [dotnet Run](/dotnet/core/tools/dotnet-run) : `dotnet run --configuration Debug`.
1. Acesse o aplicativo no navegador.
1. Coloque o foco do teclado no aplicativo, não no painel Ferramentas do desenvolvedor. O painel Ferramentas do desenvolvedor pode ser fechado quando a depuração é iniciada.
1. Selecione o seguinte atalho de teclado específico do mais alto:
   * `Shift+Alt+D`no Windows/Linux
   * `Shift+Cmd+D`no macOS

## <a name="enable-remote-debugging"></a>Habilitar depuração remota

Se a depuração remota estiver desabilitada, uma página de erro **não é possível localizar a guia do navegador depurável** será gerada pelo Chrome. A página de erro contém instruções para executar o Chrome com a porta de depuração aberta para que o proxy de depuração mais incrivelmente possa se conectar ao aplicativo. *Feche todas as instâncias do Chrome* e reinicie o Chrome conforme instruído.

## <a name="debug-the-app"></a>Depurar o aplicativo

Depois que o Chrome estiver em execução com a depuração remota habilitada, o atalho de teclado de depuração abrirá uma nova guia do depurador. Após alguns instantes, a guia **fontes** mostra uma lista dos assemblies .net no aplicativo. Expanda cada assembly e localize os arquivos de origem *. cs*/ *. Razor* disponíveis para depuração. Defina pontos de interrupção, alterne de volta para a guia do aplicativo e os pontos de interrupção serão atingidos quando o código for executado. Depois que um ponto de interrupção é atingido, etapa`F10`única () por meio da execução`F8`do código ou retomar () normalmente.

O mais incrivelmente fornece um proxy de depuração que implementa o [protocolo Chrome devtools](https://chromedevtools.github.io/devtools-protocol/) e aumenta o protocolo com o. Informações específicas de rede. Quando o atalho de teclado de depuração é pressionado, o mais um é apontado para o Chrome DevTools no proxy. O proxy se conecta à janela do navegador que você está procurando depurar (portanto, a necessidade de habilitar a depuração remota).

## <a name="browser-source-maps"></a>Mapas de origem do navegador

Os mapas de origem do navegador permitem que o navegador mapeie arquivos compilados de volta para seus arquivos de origem originais e normalmente são usados para depuração do lado do cliente. No entanto, o mais incrivelmente C# não mapeia diretamente para JavaScript/WASM. Em vez disso, o mais importante é a interpretação de IL no navegador, portanto, os mapas de origem não são relevantes.

## <a name="troubleshooting-tip"></a>Dica de solução de problemas

Se você estiver executando erros, a dica a seguir pode ajudar:

Na guia **depurador** , abra as ferramentas de desenvolvedor em seu navegador. No console do, execute `localStorage.clear()` para remover qualquer ponto de interrupção.