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
ms.openlocfilehash: 29d10b35b0855e34826c10b813a2df48cd84cfef
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711974"
---
# <a name="nmake-property-page"></a>Strona właściwości NMake
**NMake** właściwość umożliwia określenie ustawień kompilacji dla projektów NMake.  
  
Aby uzyskać więcej informacji na temat projektów NMake zobacz [Tworzenie projektu pliku reguł programu make](../ide/creating-a-makefile-project.md). Dla projektów plików reguł programu make non_Windows, zobacz [właściwości projektu pliku reguł programu make (Linux C++)](../linux/prop-pages/makefile-linux.md), [ogólne właściwości projektu (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) lub [właściwości narzędzia NMake (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).
  
**NMake** strona właściwości zawiera następujące właściwości.  
  
## <a name="uielement-list"></a>Lista elementów UI  

- **Wiersz polecenia kompilacji**

   Określa polecenie do uruchomienia po **kompilacji** jest kliknięty **kompilacji** menu.  
  
- **Wiersz poleceń rekompilacji wszystkiego**

   Określa polecenie do uruchomienia po **Kompiluj wszystko ponownie** jest kliknięty **kompilacji** menu.  
  
- **Wiersz polecenia Wyczyść**

   Określa polecenie do uruchomienia po **czysty** jest kliknięty **kompilacji** menu.  
  
- **Output**

   Określa nazwę pliku, który będzie zawierał dane wyjściowe wiersza polecenia. Domyślnie ta nazwa pliku opiera się na nazwę projektu.  
  
- **Definicje preprocesora**

   Określa wszystkie definicje preprocesora, użycia plików źródłowych. Wartość domyślna zależy od bieżącej platformy i konfiguracji.  
  
- **Ścieżka wyszukiwania plików dołączanych**

   Określa katalog, w którym kompilator wyszukuje pliki dołączane.  
  
- **Wymuszone obejmuje**

   Określa pliki, które preprocesor przetwarza automatycznie, nawet wtedy, gdy nie są uwzględniane w plikach projektu.  
  
- **Ścieżka wyszukiwania zestawu**

   Określa katalog, gdzie programu .NET Framework wyszukiwania, kiedy go próbuje rozpoznać zestawów platformy .NET.  
  
- **Wymuszone za pomocą zestawów**

   Określa zestawy, które automatycznie przetwarza programu .NET Framework.  
  
- **Dodatkowe opcje**

   Określa wszelkie dodatkowe przełączniki kompilatora dla funkcji IntelliSense do użycia podczas jej analizuje pliki języka C++.  
  
Aby uzyskać informacje o tym, jak uzyskać dostęp do **NMake** strony właściwości, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
Aby uzyskać informacje na temat programowego dostępu do elementów członkowskich tego obiektu, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)   
 [Instrukcje: włączanie funkcji IntelliSense dla projektów plików reguł programu make](../ide/how-to-enable-intellisense-for-makefile-projects.md)