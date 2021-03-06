---
title: Introdução ao ASP.NET Core
author: rick-anderson
description: Um breve tutorial que cria e executa um aplicativo básico Olá, Mundo usando o ASP.NET Core.
ms.author: riande
ms.custom: mvc
ms.date: 09/22/2019
uid: getting-started
ms.openlocfilehash: 116a22bce80257948bfcc02c03a74a4b5568b8b5
ms.sourcegitcommit: 4649814d1ae32248419da4e8f8242850fd8679a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975687"
---
# <a name="tutorial-get-started-with-aspnet-core"></a>Tutorial: Introdução ao ASP.NET Core

Este tutorial mostra como usar a interface de linha de comando do .NET Core para criar e executar um aplicativo Web ASP.NET Core.

Você aprenderá como:

> [!div class="checklist"]
> * Criar um projeto de aplicativo Web.
> * Confiar no certificado de desenvolvimento.
> * Execute o aplicativo.
> * Editar uma página do Razor.

No final, você terá um aplicativo Web de trabalho em execução no seu computador local.

![Página inicial do aplicativo Web](_static/home-page.png)

## <a name="prerequisites"></a>Pré-requisitos

[!INCLUDE[](~/includes/3.0-SDK.md)]

## <a name="create-a-web-app-project"></a>Criar um projeto de aplicativo Web

Abra um shell de comando e insira o seguinte comando:

```dotnetcli
dotnet new webapp -o aspnetcoreapp
```

O comando anterior:

* Cria um novo aplicativo Web.  
* O parâmetro `-o aspnetcoreapp` cria um diretório chamado *aspnetcoreapp* com os arquivos de origem para o aplicativo.

### <a name="trust-the-development-certificate"></a>Confiar no certificado de desenvolvimento

Confie no certificado de desenvolvimento HTTPS:

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet dev-certs https --trust
```

O comando anterior exibe a caixa de diálogo a seguir:

![Caixa de diálogo de aviso de segurança](~/getting-started/_static/cert.png)

Selecione **Sim** se você concordar com confiar no certificado de desenvolvimento.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

```dotnetcli
dotnet dev-certs https --trust
```

O comando anterior exibe a mensagem a seguir:

*Foi solicitada confiança no certificado de desenvolvimento HTTPS. Se o certificado já não for confiável, executaremos o seguinte comando:* `'sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain <<certificate>>'`

Esse comando pode solicitar que você insira sua senha para instalar o certificado no conjunto de chaves do sistema. Insira sua senha se você concordar em confiar no certificado de desenvolvimento.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Consulte a documentação para sua distribuição do Linux sobre como confiar no certificado de desenvolvimento HTTPS.

---

Para obter mais informações, confira [Confiar no certificado de desenvolvimento HTTPS do ASP.NET Core](xref:security/enforcing-ssl#trust-the-aspnet-core-https-development-certificate-on-windows-and-macos)

## <a name="run-the-app"></a>Executar o aplicativo

Execute os seguintes comandos:

```dotnetcli
cd aspnetcoreapp
dotnet watch run
```

Depois que o shell de comando indicar que o aplicativo foi iniciado, navegue até [https://localhost:5001](https://localhost:5001).

## <a name="edit-a-razor-page"></a>Editar uma página do Razor

Abra *pages/index. cshtml* e modifique e salve a página com a seguinte marcação realçada:

[!code-cshtml[](sample/index.cshtml?highlight=9)]

Navegue até [https://localhost:5001](https://localhost:5001), atualize a página e verifique se as alterações são exibidas.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:

> [!div class="checklist"]
> * Criar um projeto de aplicativo Web.
> * Confiar no certificado de desenvolvimento.
> * Execute o projeto.
> * Faça uma alteração.

Para saber mais sobre o ASP.NET Core, veja o caminho de aprendizado recomendados na introdução:

> [!div class="nextstepaction"]
> <xref:index#recommended-learning-path>
