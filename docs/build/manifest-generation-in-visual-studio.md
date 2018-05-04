---
title: Generowanie manifestu w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73b5cbe631d078dd6ee27b4f7e0a97503c36638b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-in-visual-studio"></a>Generowanie manifestu w Visual Studio
Generowanie pliku manifestu dla określonego projektu mogą być kontrolowane w projekcie **strony właściwości** okna dialogowego. Na **właściwości konfiguracji** , kliknij pozycję **konsolidatora**, następnie **plik manifestu**, następnie **Generuj Manifest**. Domyślnie nowe projekty właściwości projektu są ustawiane na generowanie pliku manifestu. Jednak jest możliwe wyłącz generowanie manifestu dla projektu przy użyciu **Generuj Manifest** właściwości projektu. Jeśli ta właściwość jest skonfigurowana **tak**, jest generowany manifestu dla tego projektu. W przeciwnym razie konsolidator ignoruje informacji o zestawie podczas rozpoznawania zależności kodu aplikacji i nie powoduje generowania manifestu.  
  
 System kompilacji w programie Visual Studio umożliwia manifestu do osadzonego w pliku końcowego binarne aplikacji lub generowane jako zewnętrzny plik. To zachowanie jest kontrolowany przez **Osadź Manifest** opcji **właściwości projektu** okna dialogowego. Aby ustawić tę właściwość, należy otworzyć **narzędziu manifestu** węzła, następnie wybierz **wejściowa i wyjściowa**. Jeśli manifest nie jest zagnieżdżony, jest generowane jako zewnętrzny plik i zapisać w tym samym katalogu co plik binarny końcowego. Jeśli plik manifestu jest osadzony, Visual Studio osadza manifesty końcowe przy użyciu poniższej procedury:  
  
1.  Kod źródłowy jest skompilowany obiekt plików, konsolidator zbiera informacje o zestawu zależnego. Podczas łączenia końcowego pliku binarnego, konsolidator generuje pośredniego manifestu, który jest później używany do generowania manifestu końcowego.  
  
2.  Po zakończeniu pośredni manifestu i połączeń, narzędzia manifestu zostaną wykonane końcowe manifestu i zapisać go jako plik.  
  
3.  Projekt systemu kompilacji, a następnie wykrywa, czy manifest wygenerowany przez narzędzie manifestu zawiera różne informacje niż manifest już osadzone w danych binarnych.  
  
4.  Jeśli manifest osadzone w pliku binarnego różni się od manifest wygenerowany przez narzędzie manifestu lub dane binarne nie zawiera osadzonego manifestu, Visual Studio wywoła konsolidator jeszcze raz do osadzenia zewnętrznego pliku manifestu w danych binarnych jako zasób.  
  
5.  Jeśli manifest osadzone w danych binarnych jest taka sama jak manifest wygenerowany przez narzędzie manifestu, kompilacja będzie do następnych kroków kompilacji.  
  
 Manifest jest osadzony w końcowym dane binarne jako zasób tekstu i można je wyświetlić, otwierając plik binarny końcowego jako plik w programie Visual Studio. Aby upewnić się, że manifest wskazuje poprawne bibliotek, wykonaj czynności opisane w [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) lub wykonaj sugestie opisanego w [Rozwiązywanieproblemów](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: osadzanie manifestu w aplikacji C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [Informacje o zestawach prywatnych](http://msdn.microsoft.com/library/ff951638)   
 [Narzędzie manifestu](http://msdn.microsoft.com/library/aa375649)   
 [Ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)