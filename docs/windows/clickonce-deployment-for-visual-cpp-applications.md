---
title: Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4408db9d129c03ee5df9b006b03c6586df02afb1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513764"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++

Program Visual Studio oferuje dwie różne technologie wdrażania aplikacji systemu Windows: Wdrożenie ClickOnce lub wdrożenie [Instalator Windows](/windows/win32/Msi/windows-installer-portal) .

## <a name="clickonce-deployment-in-c"></a>Wdrożenie ClickOnce wC++

Środowisko programistyczne Visual C++ Studio C++ nie obsługuje bezpośrednio wdrażania projektów programu z użyciem technologii ClickOnce, ale dostępne są narzędzia do korzystania z nich.

> [!NOTE]
>  Program Visual Studio obsługuje ClickOnce w wizualizacjach C# i Visual Basic środowiskach deweloperskich. Jeśli projekt programu Visual C++ Studio jest zależnością projektu wizualnego C# , można opublikować aplikację (łącznie z jej zależnościami) przy użyciu wdrożenia ClickOnce ze środowiska deweloperskiego Visual C# .

Aby C++ wdrożyć aplikację wizualną przy użyciu technologii ClickOnce, musisz najpierw skompilować [manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) i [manifest wdrożenia ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) przy użyciu programu [Mage. exe (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) lub jego graficznego użytkownika wersja interfejsu (Aby uzyskać informacje, zobacz [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).

Należy najpierw użyć programu Mage. exe do skompilowania manifestu aplikacji; otrzymany plik będzie miał rozszerzenie. manifest. Następnie należy użyć programu Mage. exe do skompilowania manifestu wdrożenia. otrzymany plik będzie miał rozszerzenie. Application. Następnie Podpisz manifesty.

Manifest aplikacji musi określać procesor docelowy (**x86**, **x64**lub **ARM**). Aby uzyskać informacje na temat tych opcji, zobacz temat [wdrażanie wymagań wstępnych dla aplikacji 64-bitowych](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) .

Ponadto nazwy aplikacji i manifestów wdrożenia muszą być inne niż nazwa C++ aplikacji. Pozwala to uniknąć konfliktu między manifestem aplikacji utworzonym przez program Mage. exe i zewnętrznym manifestem, który C++ jest częścią aplikacji.

Wdrożenie będzie wymagało zainstalowania wszystkich bibliotek wizualizacji C++ , od których zależy aplikacja. Aby określić zależności dla konkretnej aplikacji, można użyć narzędzia zależne. exe lub narzędzie polecenia DUMPBIN z opcją/DEPENDENTS. Aby uzyskać więcej informacji na temat zależności, zobacz [Omówienie zależności aplikacji C++ wizualnej](understanding-the-dependencies-of-a-visual-cpp-application.md). Może być konieczne uruchomienie programu VCRedist. exe; to narzędzie instaluje biblioteki C++ wizualne na komputerze docelowym.

Może być również konieczne skompilowanie programu inicjującego (Instalator wymagań wstępnych) dla aplikacji w celu wdrożenia składników wymaganych wstępnie. Aby uzyskać informacje na temat programu inicjującego, zobacz [Tworzenie pakietów](/visualstudio/deployment/creating-bootstrapper-packages)programu inicjującego.

Aby uzyskać bardziej szczegółowy opis technologii, zobacz [zabezpieczenia i wdrażanie aplikacji ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Aby zapoznać się ze szczegółowym przykładem wdrażania [ClickOnce, zobacz Przewodnik: Ręczne wdrażanie aplikacji](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)ClickOnce.

## <a name="see-also"></a>Zobacz także

[Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[MakeCert. exe (narzędzie tworzenia certyfikatów)](/windows/win32/SecCrypto/makecert)<br>
[Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)<br>
[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
