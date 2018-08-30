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
ms.openlocfilehash: 6f927e153c25b41b48b783281a36dd2705e42006
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205803"
---
# <a name="manifest-generation-in-visual-studio"></a>Generowanie manifestu w Visual Studio
Generowanie pliku manifestu dla konkretnego projektu mogą być kontrolowane w projekcie **stron właściwości** okna dialogowego. Na **właściwości konfiguracji** kliknij pozycję **konsolidatora**, następnie **pliku manifestu**, następnie **Generuj Manifest**. Domyślnie nowe projekty właściwości projektu są ustawione na wygenerować plik manifestu. Jednak istnieje możliwość wyłączyć generowanie manifestu dla projektu za pomocą **Generuj Manifest** właściwość projektu. Jeśli ta właściwość jest równa **tak**, generowany jest manifestu dla tego projektu. W przeciwnym razie konsolidator ignoruje informacje o zestawie podczas rozpoznawania zależności kodu aplikacji i nie powoduje generowania manifestu.  
  
 System kompilacji w programie Visual Studio umożliwia manifest osadzone w pliku końcowego binarnych aplikacji lub generowane jako zewnętrznego pliku. To zachowanie jest kontrolowany przez **osadzanie manifestu** opcji **właściwości projektu** okna dialogowego. Aby ustawić tę właściwość, należy otworzyć **narzędziu manifestu** węzła, następnie wybierz pozycję **danych wejściowych i wyjściowych**. Jeśli manifest nie jest zagnieżdżony, jest generowane jako zewnętrznego pliku i zapisany w tym samym katalogu co końcowym pliku binarnym. Jeśli manifest jest osadzony, Visual Studio osadza końcowego manifesty przy użyciu następującego procesu:  
  
1.  Kod źródłowy jest skompilowany w plikach obiektu, konsolidator zbiera informacje o zestawu zależnego. Podczas łączenia końcowym pliku binarnym, konsolidator generuje manifest pośredniego, który jest później używany do generowania końcowego manifestu.  
  
2.  Po zakończeniu wartość pośredni manifestu i łączenia, narzędzie manifestu zostaną wykonane końcowego manifestu i zapisz go jako plik.  
  
3.  Projekt systemu kompilacji, a następnie wykrywa, czy manifest wygenerowany przez narzędzie manifestu zawiera różne informacje niż manifest już osadzone w pliku binarnym.  
  
4.  Jeśli manifestem osadzonym w pliku binarnym różni się od manifest wygenerowany przez narzędzie manifestu, lub dane binarne nie zawiera manifestu osadzonego, programu Visual Studio będzie wywoływać konsolidator jeszcze raz można osadzić zewnętrznego pliku manifestu w danych binarnych jako zasób.  
  
5.  Jeśli manifestem osadzonym w pliku binarnym jest taka sama jak manifest wygenerowany przez narzędzie manifestu, kompilacja będzie następne kroki kompilacji.  
  
 Manifest jest osadzony w końcowym pliku binarnym jako zasób tekstu i można je wyświetlić, otwierając końcowy danych binarnych jako plik w programie Visual Studio. Aby upewnić się, że manifest wskazuje prawidłowy bibliotek, wykonaj czynności opisane w [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) lub postępować zgodnie z sugestii opisanego w [Rozwiązywanieproblemów](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: osadzanie manifestu w aplikacji C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [Zestawy prywatne informacje](/windows/desktop/SbsCs/about-private-assemblies-)   
 [Narzędzie manifestu](/windows/desktop/SbsCs/mt-exe)   
 [Ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)