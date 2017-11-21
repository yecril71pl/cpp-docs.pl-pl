---
title: "Wdrożenie ClickOnce dla aplikacji Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 454bc2d4fd19568f526881208da77deabbe72087
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++
Program Visual Studio oferuje dwa różne technologie wdrażania aplikacji systemu Windows: wdrażania ClickOnce lub [Instalatora Windows](http://msdn.microsoft.com/library/cc185688) wdrożenia.  
  
## <a name="clickonce-deployment-in-c"></a>Wdrożenie ClickOnce w języku C++  
 Środowisko projektowe Visual C++ nie obsługuje bezpośrednio wdrażania projektów Visual C++ za pomocą technologii ClickOnce, ale narzędzia są dostępne z niego korzystać.  
  
> [!NOTE]
>  W środowisku programowania Visual C# i Visual Basic, Visual Studio obsługuje technologii ClickOnce. Projekt Visual C++ w przypadku zależności projektu Visual C#, można opublikować aplikacji (wraz z zależnościami) przy użyciu wdrażania ClickOnce środowiska programowania Visual C#.  
  
 Aby wdrażanie aplikacji Visual C++ za pomocą aplikacji ClickOnce, najpierw należy utworzyć [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) i [Manifest wdrażania ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) przy użyciu [Mage.exe (Manifest Generowanie i narzędzia do edycji)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) lub jego graficznego interfejsu użytkownika programu (Aby uzyskać informacje, zobacz [MageUI.exe (Generowanie manifestu i edytowania narzędzia graficzne klienta)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).  

  
 Użyj Mage.exe do tworzenia manifest aplikacji; Wynikowy plik ma rozszerzenie ".manifest". Następnie użyj Mage.exe do tworzenia manifest wdrażania; Wynikowy plik ma rozszerzenie .application. Następnie zaloguj manifestach.  
  
 Manifest aplikacji musi określać procesor docelowy (**x86**, **x64**, lub **ARM**). Zobacz [wdrażanie wymagania wstępne dotyczące aplikacji 64-bitowych](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) informacji na temat tych opcji.  
  
 Ponadto nazwa manifestów aplikacji i wdrożenia musi być inna niż nazwa aplikacji C++. Dzięki temu można uniknąć konfliktu między utworzone przez Mage.exe manifest aplikacji i manifest zewnętrznych, będącej częścią aplikacji C++.  
  
 Wdrożenie należy zainstalować żadnych bibliotek języka Visual C++, od których zależy aplikacja. Aby określić zależności dla wybranej aplikacji, można używać depends.exe lub dumpbin — narzędzie z opcją /DEPENDENTS. Aby uzyskać więcej informacji o zależnościach, zobacz [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Może być konieczne uruchomienie VCRedist.exe; to narzędzie instaluje bibliotek języka Visual C++ na komputerze docelowym.  
  
 Może być również konieczne kompilacji programu inicjującego (wymagań wstępnych Instalatora) dla aplikacji do wdrożenia składników wymaganych wstępnie; Aby uzyskać informacje na inicjujący, zobacz [tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages).  
  
 Aby uzyskać bardziej szczegółowy opis technologii, zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowy przykład wdrażania ClickOnce, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Generowanie manifestu i edytowania narzędzia, klient grafiki)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Wdrożenia Instalatora Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Tworzenie pakietów programu inicjującego](/visualstudio/deployment/creating-bootstrapper-packages)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Macierzysty i współdziałaniu .NET](../dotnet/native-and-dotnet-interoperability.md)