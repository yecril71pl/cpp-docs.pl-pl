---
title: Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: f78aca6621462ccbd86cfe09ae71b715b5e56f09
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448464"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++

Program Visual Studio oferuje dwie różne technologie wdrażania aplikacji Windows: Wdrażanie ClickOnce lub [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal) wdrożenia.

## <a name="clickonce-deployment-in-c"></a>Wdrożenie ClickOnce w języku C++

Element wizualny C++ środowiska programowania nie obsługuje bezpośrednio wdrażania programu Visual Studio C++ projektów za pomocą technologii ClickOnce, ale narzędzia są dostępne z niego korzystać.

> [!NOTE]
>  Program Visual Studio obsługuje ClickOnce w środowiskach programistycznych języka Visual C# i Visual Basic. Jeśli programu Visual Studio C++ projekt jest zależność wizualizacji C# projektu, możesz opublikować aplikację (łącznie z jej zależnościami) za pomocą wdrażania ClickOnce z wizualizacji C# środowiska deweloperskiego.

Do wdrażania aplikacji Visual C++ przy użyciu aplikacji ClickOnce, najpierw trzeba utworzyć [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) i [Manifest wdrażania ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) przy użyciu [Mage.exe (Manifest Generowanie i narzędzia do edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) lub jego graficznego interfejsu użytkownika programu (Aby uzyskać informacje, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).

Użyj Mage.exe, aby utworzyć manifest aplikacji; Wynikowy plik będzie miał rozszerzenie .manifest. Następnie użyj Mage.exe, aby utworzyć manifest wdrożenia; Wynikowy plik będzie miał rozszerzenie .application. Następnie Podpisz manifesty.

Manifest aplikacji musi określić procesor docelowy (**x86**, **x64**, lub **ARM**). Zobacz [wdrażanie wymagania wstępne dla aplikacji 64-bitowych](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) informacji na temat tych opcji.

Ponadto nazwy manifestów aplikacji i wdrożenia musi być inna niż nazwa aplikacji w języku C++. Pozwala to uniknąć konfliktu między manifestem aplikacji utworzonym przez Mage.exe i manifestem zewnętrznym, który jest częścią aplikacji C++.

Wdrożenia, musisz zainstalować wszelkie biblioteki Visual C++, od których zależy aplikacja. W celu określenia zależności dla konkretnej aplikacji, można użyć depends.exe lub narzędzia DUMPBIN z dependents. Aby uzyskać więcej informacji o zależnościach, zobacz [poznanie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Konieczne może być uruchomienie VCRedist.exe; to narzędzie instaluje biblioteki Visual C++ na komputerze docelowym.

Może być również konieczne zbudowanie programu inicjującego (wymagania wstępne Instalatora) dla aplikacji, aby wdrożyć wstępnie wymagane składniki; Aby uzyskać informacji na temat program inicjujący, zobacz [tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages).

Aby uzyskać bardziej szczegółowy opis technologii, zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowy przykład wdrażania ClickOnce, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).

## <a name="see-also"></a>Zobacz także

[Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[MakeCert.exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/windows/desktop/aa386968)<br>
[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)<br>
[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
