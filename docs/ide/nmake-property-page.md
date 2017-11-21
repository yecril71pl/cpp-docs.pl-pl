---
title: "Strona właściwości NMake | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs: C++
helpviewer_keywords: NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c487cf7218f11ba6a6a27ddcf5e7b6b575b1499
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-property-page"></a>Strona właściwości NMake
**NMake** strony właściwości pozwala określić ustawienia kompilacji dla projektów NMake.  
  
 Aby uzyskać więcej informacji na temat projektów NMake zobacz [Tworzenie projektu pliku reguł programu make](../ide/creating-a-makefile-project.md).  
  
 **NMake** strona zawiera następujące właściwości.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Wiersz polecenia kompilacji**  
 Określa polecenie, które można uruchamiać, gdy **kompilacji** kliknięciu **kompilacji** menu.  
  
 **Wiersz poleceń rekompilacji wszystkiego**  
 Określa polecenie, które można uruchamiać, gdy **rekompilacji wszystkiego** kliknięciu **kompilacji** menu.  
  
 **Wiersz poleceń oczyszczenia**  
 Określa polecenie, które można uruchamiać, gdy **wyczyść** kliknięciu **kompilacji** menu.  
  
 **Dane wyjściowe**  
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
 [Porady: włączenie funkcji IntelliSense dla projektów pliku reguł programu make](../ide/how-to-enable-intellisense-for-makefile-projects.md)