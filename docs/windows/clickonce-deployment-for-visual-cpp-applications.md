---
title: Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4726fda8c5eca70ce7acde19f141a7c096395e95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316607"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++

Program Visual Studio udostępnia dwie różne technologie wdrażania aplikacji systemu Windows: ClickOnce wdrożenia lub wdrożenia [Instalatora Windows.](/windows/win32/Msi/windows-installer-portal)

## <a name="clickonce-deployment-in-c"></a>ClickOnce Wdrożenia w języku C++

Środowisko programistyczne języka Visual C++ nie obsługuje bezpośrednio wdrażania projektów programu Visual Studio C++ za pomocą funkcji ClickOnce, ale dostępne są narzędzia do jego używania.

> [!NOTE]
> Visual Studio obsługuje ClickOnce w środowiskach programowania Visual C# i Visual Basic. Jeśli projekt Programu Visual Studio C++ jest zależnością projektu visual C#, można opublikować aplikację (w tym jej zależności) przy użyciu clickonce wdrożenia ze środowiska programistycznego języka Visual C#.

Aby wdrożyć aplikację Visual C++ przy użyciu ClickOnce, należy najpierw utworzyć [manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) i [manifest wdrożenia ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) przy użyciu [mage.exe (narzędzie do generowania manifestu i edycji)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) lub jego graficznej wersji interfejsu użytkownika (aby uzyskać informacje, zobacz [MageUI.exe (Narzędzie do generowania manifestu i edycji, Klient graficzny).](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)

Najpierw używasz Mage.exe do tworzenia manifestu aplikacji; wynikowy plik będzie miał rozszerzenie .manifest. Następnie należy użyć Mage.exe do utworzenia manifestu wdrożenia; wynikowy plik będzie miał rozszerzenie .application. Następnie podpisz manifesty.

Manifest aplikacji musi określać procesor docelowy (**x86**, **x64**lub **ARM**). Zobacz [Wdrażanie wymagań wstępnych dla aplikacji 64-bitowych, aby](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) uzyskać informacje na temat tych opcji.

Ponadto nazwa manifestów aplikacji i wdrażania musi się różnić od nazwy aplikacji C++. Pozwala to uniknąć konfliktu między manifestu aplikacji utworzone przez Mage.exe i manifestu zewnętrznego, który jest częścią aplikacji C++.

Wdrożenie będzie musiał zainstalować wszystkie biblioteki języka Visual C++, od których zależy aplikacja. Aby określić zależności dla określonej aplikacji, można użyć depends.exe lub dumpbin narzędzie z /DEPENDENTS opcji. Aby uzyskać więcej informacji na temat zależności, zobacz [Opis zależności aplikacji Visual C++.](understanding-the-dependencies-of-a-visual-cpp-application.md) Może być konieczne uruchomienie pliku VCRedist.exe; to narzędzie instaluje biblioteki języka Visual C++ na komputerze docelowym.

Może być również konieczne tworzenie programu uruchamiający (instalator wymagań wstępnych) dla aplikacji do wdrażania składników wymagań wstępnych; aby uzyskać informacje na temat inicjowania, zobacz [Tworzenie pakietów bootstrapperów](/visualstudio/deployment/creating-bootstrapper-packages).

Aby uzyskać bardziej szczegółowy opis technologii, zobacz [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowy przykład wdrożenia ClickOnce, zobacz [Instruktaż: Ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).

## <a name="see-also"></a>Zobacz też

[Mage.exe (narzędzie do generowania manifestów i edycji)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (narzędzie do generowania manifestu i edycji, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Plik Makecert.exe (narzędzie do tworzenia certyfikatów)](/windows/win32/SecCrypto/makecert)<br>
[Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)<br>
[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
