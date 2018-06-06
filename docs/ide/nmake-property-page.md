---
title: Strona właściwości NMake (Windows C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs:
- C++
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f156d69467f00c4c4a62ec84d3b870e2999d7115
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33327463"
---
# <a name="nmake-property-page"></a>Strona właściwości NMake
**NMake** strony właściwości pozwala określić ustawienia kompilacji dla projektów NMake.  
  
 Aby uzyskać więcej informacji na temat projektów NMake zobacz [Tworzenie projektu pliku reguł programu make](../ide/creating-a-makefile-project.md). Non_Windows projekty pliku reguł programu make dla [właściwości projektu pliku reguł programu make (Linux C++)](../linux/prop-pages/makefile-linux.md), [ogólne właściwości projektu (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) lub [właściwości NMake (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).
  
 **NMake** strona zawiera następujące właściwości.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Wiersz polecenia kompilacji**  
 Określa polecenie, które można uruchamiać, gdy **kompilacji** kliknięciu **kompilacji** menu.  
  
 **Wiersz poleceń rekompilacji wszystkiego**  
 Określa polecenie, które można uruchamiać, gdy **rekompilacji wszystkiego** kliknięciu **kompilacji** menu.  
  
 **Wiersz poleceń oczyszczenia**  
 Określa polecenie, które można uruchamiać, gdy **wyczyść** kliknięciu **kompilacji** menu.  
  
 **Output**  
 Określa nazwę pliku, który będzie zawierać dane wyjściowe dla wiersza polecenia. Domyślnie ta nazwa pliku opiera się na nazwę projektu.  
  
 **Definicje preprocesora**  
 Określa wszystkie definicje preprocesora, że Użyj plików źródłowych. Wartość domyślna zależy od bieżącej platformy i konfiguracji.  
  
 **Ścieżki wyszukiwania załączania**  
 Określa katalog, w którym kompilator szuka plików dołączanych.  
  
 **Wymuszone obejmuje**  
 Określa pliki, które preprocesora przetwarza automatycznie, nawet jeśli nie są uwzględniane w plikach projektu.  
  
 **Ścieżki wyszukiwania zestawu**  
 Określa katalog, w którym wyszukuje podczas obliczania programu .NET Framework go próbuje rozpoznać zestawów platformy .NET.  
  
 **Wymuszone używanie zestawów**  
 Określa zestawy, które automatycznie przetwarza programu .NET Framework.  
  
 **Dodatkowe opcje**  
 Określa wszelkie dodatkowe przełączniki kompilatora dla IntelliSense do użycia podczas jego analizowania plików C++.  
  
 Aby uzyskać informacje dotyczące dostępu do **NMake** strony właściwości, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
 Aby dowiedzieć się, jak programowo dostęp do członków tego obiektu, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)   
 [Instrukcje: włączanie funkcji IntelliSense dla projektów plików reguł programu make](../ide/how-to-enable-intellisense-for-makefile-projects.md)