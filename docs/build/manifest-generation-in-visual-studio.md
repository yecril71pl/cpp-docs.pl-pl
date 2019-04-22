---
title: Generowanie manifestu w Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781682"
---
# <a name="manifest-generation-in-visual-studio"></a>Generowanie manifestu w Visual Studio

Generowanie pliku manifestu dla konkretnego projektu mogą być kontrolowane w projekcie **stron właściwości** okna dialogowego. Na **właściwości konfiguracji** kliknij pozycję **konsolidatora**, następnie **pliku manifestu**, następnie **Generuj Manifest**. Domyślnie nowe projekty właściwości projektu są ustawione na wygenerować plik manifestu. Jednak istnieje możliwość wyłączyć generowanie manifestu dla projektu za pomocą **Generuj Manifest** właściwość projektu. Jeśli ta właściwość jest równa **tak**, generowany jest manifestu dla tego projektu. W przeciwnym razie konsolidator ignoruje informacje o zestawie podczas rozpoznawania zależności kodu aplikacji i nie powoduje generowania manifestu.

System kompilacji w programie Visual Studio umożliwia manifest osadzone w pliku końcowego binarnych aplikacji lub generowane jako zewnętrznego pliku. To zachowanie jest kontrolowany przez **osadzanie manifestu** opcji **właściwości projektu** okna dialogowego. Aby ustawić tę właściwość, należy otworzyć **narzędziu manifestu** węzła, następnie wybierz pozycję **danych wejściowych i wyjściowych**. Jeśli manifest nie jest zagnieżdżony, jest generowane jako zewnętrznego pliku i zapisany w tym samym katalogu co końcowym pliku binarnym. Jeśli manifest jest osadzony, Visual Studio osadza końcowego manifesty przy użyciu następującego procesu:

1. Kod źródłowy jest skompilowany w plikach obiektu, konsolidator zbiera informacje o zestawu zależnego. Podczas łączenia końcowym pliku binarnym, konsolidator generuje manifest pośredniego, który jest później używany do generowania końcowego manifestu.

1. Po zakończeniu wartość pośredni manifestu i łączenia, narzędzie manifestu zostaną wykonane końcowego manifestu i zapisz go jako plik.

1. Projekt systemu kompilacji, a następnie wykrywa, czy manifest wygenerowany przez narzędzie manifestu zawiera różne informacje niż manifest już osadzone w pliku binarnym.

1. Jeśli manifestem osadzonym w pliku binarnym różni się od manifest wygenerowany przez narzędzie manifestu, lub dane binarne nie zawiera manifestu osadzonego, programu Visual Studio będzie wywoływać konsolidator jeszcze raz można osadzić zewnętrznego pliku manifestu w danych binarnych jako zasób.

1. Jeśli manifestem osadzonym w pliku binarnym jest taka sama jak manifest wygenerowany przez narzędzie manifestu, kompilacja będzie następne kroki kompilacji.

Manifest jest osadzony w końcowym pliku binarnym jako zasób tekstu i można je wyświetlić, otwierając końcowy danych binarnych jako plik w programie Visual Studio. Aby upewnić się, że manifest wskazuje prawidłowy bibliotek, wykonaj czynności opisane w [poznanie zależności aplikacji Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) lub postępować zgodnie z sugestii opisanego w [Rozwiązywanieproblemów](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) sekcji.

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
