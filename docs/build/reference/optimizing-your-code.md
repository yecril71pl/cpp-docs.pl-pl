---
title: Optymalizacja kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8b18ba4ce00eb751d8f30debbab3e87b9cce53e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378980"
---
# <a name="optimizing-your-code"></a>Optymalizacja kodu

Dzięki optymalizacji pliku wykonywalnego, można osiągnąć kompromis między szybkość wykonywania szybkiego i rozmiar mały kod. W tym temacie omówiono niektóre mechanizmy, które Visual C++ w celu zapewnienia optymalizacji kodu.

## <a name="language-features"></a>Funkcje językowe

W poniższych tematach opisano niektóre funkcje optymalizacji w języku C/C++.

[Optymalizacja pragm i słów kluczowych](../../build/reference/optimization-pragmas-and-keywords.md)  
Lista słowa kluczowe i pragmy, że można użyć w kodzie do zwiększenia wydajności.

[Opcje kompilatora w rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md)  
Lista **/O** opcje kompilatora, które dotyczą wykonywania rozmiar szybkości łącza lub kodu.

[Deklarator odwołania do wartości R: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
Odwołania wartościowane prawostronnie obsługuje wykonania *Przenieś semantyki*. Jeśli przeniesienie semantyki są używane do implementowania biblioteki szablonów i wydajności aplikacji korzystających z tych szablonów może znacznie poprawić.

### <a name="the-optimize-pragma"></a>Pragma Optymalizacja

Jeśli sekcji zoptymalizowanego kodu powoduje występowanie błędów i spowolnienie, możesz użyć [zoptymalizować](../../preprocessor/optimize.md) pragma, aby wyłączyć funkcję optymalizacji dla tej sekcji.

Dołączyć kod między dwoma pragm, jak pokazano poniżej:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Rozwiązania w zakresie programowania

Podczas kompilowania kodu przy użyciu optymalizacji można zauważyć dodatkowych komunikatów ostrzegawczych. Jest to zachowanie oczekiwane, ponieważ ostrzeżenia odnosić się tylko do zoptymalizowanego kodu. Wiele problemów optymalizacji można uniknąć, jeżeli uwzględnianie tych ostrzeżeń.

Paradoxically optymalizacji programu szybkości może spowodować kodu działać wolniej. Jest to spowodowane niektórych optymalizacji dla szybkości zwiększyć rozmiar kodu. Na przykład ze śródwierszowaniem funkcji eliminuje obciążenie wywołania funkcji. Jednak ze śródwierszowaniem zbyt dużej ilości kodu może Twoje program był tak duży, że numer strony pamięci wirtualnej błędów zwiększa. W związku z tym szybkości zdobytych wyeliminowanie wywołania funkcji mogą zostać utracone do wymiany pamięci.

W poniższych tematach opisano dobrych praktyk programowania.

[Wskazówki dotyczące poprawiania kodu wrażliwego na czas](../../build/reference/tips-for-improving-time-critical-code.md)  
Techniki tworzenia kodu lepiej może zapewnić lepszą wydajność. W tym temacie sugeruje kodowania techniki, które mogą pomóc Ci upewnij się, że pomyślnie wykonać części kodu wrażliwego na czas.

[Najlepsze rozwiązania dotyczące optymalizacji](../../build/reference/optimization-best-practices.md)  
Zawiera ogólne wskazówki dotyczące jak najlepiej zoptymalizować aplikacji.

## <a name="debugging-optimized-code"></a>Debugowanie zoptymalizowanego kodu

Optymalizacja może zmienić kod, który został utworzony przez kompilator, dlatego zaleca debugowania aplikacji i mierzenie jego wydajności i następnie optymalizacji kodu.

Podstawowe informacje o tym, jak można debugować można znaleźć w następujących tematach.

- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Typowe problemy podczas tworzenia kompilacji wydania](../../build/reference/common-problems-when-creating-a-release-build.md)

Poniższe tematy zawierają bardziej zaawansowane informacje dotyczące debugowania.

- [Porady: debugowanie zoptymalizowanego kodu](/visualstudio/debugger/how-to-debug-optimized-code)

- [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Poniższe tematy zawierają informacje na temat optymalizacji tworzenia ładowania oraz wykonywania kodu.

- [Poprawianie wydajności kompilatora](../../build/reference/improving-compiler-throughput.md)

- [Korzystanie z nazwy funkcji bez () nie tworzy kodu](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optymalizacja wbudowanego asemblera](../../assembler/inline/optimizing-inline-assembly.md)

- [Określanie optymalizacji kompilatora dla projektu ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Jakich technik optymalizacji należy użyć, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)  
