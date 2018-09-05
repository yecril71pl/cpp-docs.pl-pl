---
title: Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82a290eb7695bbcd7c03cda0351445519352e80a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677727"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++
Program Visual Studio oferuje dwie różne technologie wdrażania aplikacji Windows: Wdrażanie ClickOnce lub [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal) wdrożenia.  
  
## <a name="clickonce-deployment-in-c"></a>Wdrożenie ClickOnce w języku C++  
 Środowisko projektowe Visual C++ nie obsługuje bezpośrednio wdrażania projektów Visual C++ za pomocą technologii ClickOnce, ale narzędzia są dostępne z niego korzystać.  
  
> [!NOTE]
>  Program Visual Studio obsługuje ClickOnce w środowiskach programistycznych języka Visual C# i Visual Basic. Jeśli projekt Visual C++ jest zależność projekt Visual C#, możesz opublikować aplikację (łącznie z jej zależnościami) za pomocą wdrażania ClickOnce ze środowiska projektowego Visual C#.  
  
 Do wdrażania aplikacji Visual C++ przy użyciu aplikacji ClickOnce, najpierw trzeba utworzyć [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) i [Manifest wdrażania ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) przy użyciu [Mage.exe (Manifest Generowanie i narzędzia do edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) lub jego graficznego interfejsu użytkownika programu (Aby uzyskać informacje, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).  

  
 Użyj Mage.exe, aby utworzyć manifest aplikacji; Wynikowy plik będzie miał rozszerzenie .manifest. Następnie użyj Mage.exe, aby utworzyć manifest wdrożenia; Wynikowy plik będzie miał rozszerzenie .application. Następnie Podpisz manifesty.  
  
 Manifest aplikacji musi określić procesor docelowy (**x86**, **x64**, lub **ARM**). Zobacz [wdrażanie wymagania wstępne dla aplikacji 64-bitowych](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) informacji na temat tych opcji.  
  
 Ponadto nazwy manifestów aplikacji i wdrożenia musi być inna niż nazwa aplikacji w języku C++. Pozwala to uniknąć konfliktu między manifestem aplikacji utworzonym przez Mage.exe i manifestem zewnętrznym, który jest częścią aplikacji C++.  
  
 Wdrożenia, musisz zainstalować wszelkie biblioteki Visual C++, od których zależy aplikacja. W celu określenia zależności dla konkretnej aplikacji, można użyć depends.exe lub narzędzia DUMPBIN z dependents. Aby uzyskać więcej informacji o zależnościach, zobacz [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Konieczne może być uruchomienie VCRedist.exe; to narzędzie instaluje biblioteki Visual C++ na komputerze docelowym.  
  
 Może być również konieczne zbudowanie programu inicjującego (wymagania wstępne Instalatora) dla aplikacji, aby wdrożyć wstępnie wymagane składniki; Aby uzyskać informacji na temat program inicjujący, zobacz [tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages).  
  
 Aby uzyskać bardziej szczegółowy opis technologii, zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowy przykład wdrażania ClickOnce, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest narzędzie generowania i edytowania, graficzny klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages)   
 [Programowanie .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)