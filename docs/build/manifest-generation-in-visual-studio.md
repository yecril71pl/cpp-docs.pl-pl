---
title: Generowanie manifestu w Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273367"
---
# <a name="manifest-generation-in-visual-studio"></a>Generowanie manifestu w Visual Studio

Generowanie pliku manifestu dla określonego projektu może być kontrolowane w oknie dialogowym **strony właściwości** projektu. Na karcie **Właściwości konfiguracji** kliknij przycisk **konsolidator**, a następnie **plik manifestu**, a następnie **Generuj manifest**. Domyślnie właściwości projektu nowych projektów są ustawione tak, aby generować plik manifestu. Można jednak wyłączyć generowanie manifestu dla projektu przy użyciu właściwości **generowanie manifestu** projektu. Gdy ta właściwość ma wartość **Yes (tak**), zostanie wygenerowany manifest dla tego projektu. W przeciwnym razie konsolidator ignoruje informacje o zestawie podczas rozpoznawania zależności od kodu aplikacji i nie generuje manifestu.

System kompilacji w programie Visual Studio umożliwia osadzenie manifestu w końcowym pliku aplikacji binarnej lub wygenerowanie go jako pliku zewnętrznego. To zachowanie jest kontrolowane przez opcję **Osadź manifest** w oknie dialogowym **właściwości projektu** . Aby ustawić tę właściwość, Otwórz węzeł **narzędzie manifestu** , a następnie wybierz pozycję **dane wejściowe i wyjściowe**. Jeśli manifest nie jest osadzony, zostanie wygenerowany jako plik zewnętrzny i zapisany w tym samym katalogu, co w przypadku finalnego pliku binarnego. Jeśli manifest jest osadzony, program Visual Studio osadzi końcowe manifesty przy użyciu następującego procesu:

1. Po skompilowaniu kodu źródłowego w plikach obiektów konsolidator zbiera zależne informacje o zestawie. Podczas łączenia końcowego pliku binarnego konsolidator generuje manifest pośredni, który jest używany później do generowania manifestu końcowego.

1. Po zakończeniu pośredniego manifestu i konsolidacji narzędzie manifestu zostanie wykonane w celu scalenia końcowego manifestu i zapisania go jako pliku zewnętrznego.

1. System kompilacji projektu wykrywa, czy manifest wygenerowany przez narzędzie manifestu zawiera inne informacje niż manifest już osadzony w pliku binarnym.

1. Jeśli manifest osadzony w pliku binarnym różni się od manifestu wygenerowanego przez narzędzie manifestu lub plik binarny nie zawiera osadzonego manifestu, program Visual Studio wywołaje jeden więcej czasu w celu osadzenia zewnętrznego pliku manifestu w formacie binarnym jako zasób.

1. Jeśli manifest osadzony w pliku binarnym jest taki sam jak manifest wygenerowany przez narzędzie manifestu, kompilacja będzie kontynuowana do następnych kroków kompilacji.

Manifest jest osadzony w końcowym pliku binarnym jako zasób tekstowy i można go wyświetlić, otwierając ostateczną wartość binarną jako plik w programie Visual Studio. Aby zapewnić, że manifest wskazuje poprawne biblioteki, wykonaj kroki opisane w artykule [Opis zależności aplikacji Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) lub postępuj zgodnie z sugestiami opisanymi w sekcji [Rozwiązywanie problemów](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) .

## <a name="see-also"></a>Zobacz też

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
