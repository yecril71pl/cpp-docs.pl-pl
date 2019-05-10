---
title: Optymalizacja kodu
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: f44fb734c8441e10b656c5326c8df4bf6879499a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220177"
---
# <a name="optimizing-your-code"></a>Optymalizacja kodu

Dzięki optymalizacji pliku wykonywalnego, można osiągnąć kompromis między szybkiego wykonywania szybkości i rozmiaru mały kod. W tym temacie omówiono niektóre mechanizmy, które program Visual Studio udostępnia ułatwiające optymalizację kodu.

## <a name="language-features"></a>Funkcje językowe

W następujących tematach opisano niektóre funkcje optymalizacji w języku C/C++.

[Optymalizacja Pragm i słów kluczowych](optimization-pragmas-and-keywords.md) \
Lista słowa kluczowe i pragmy, można użyć w kodzie, aby zwiększyć wydajność.

[Opcje kompilatora w rozbiciu na kategorie](reference/compiler-options-listed-by-category.md) \
Lista **/O** opcje kompilatora, które dotyczą wykonywania rozmiar szybkość lub kodu.

[Deklarator odwołania do wartości r: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
Odwołania Rvalue wspierają implementację *semantyki przenoszenia*. Jeśli przenoszenie semantyki są używane do implementowania biblioteki szablonów, wydajność aplikacji, które używają tych szablonów może znacznie poprawić.

### <a name="the-optimize-pragma"></a>Pragma — Optymalizuj

Jeśli zoptymalizowane części kodu powoduje, że błędy lub spowalniają działanie, możesz użyć [zoptymalizować](../preprocessor/optimize.md) pragma może wyłączyć optymalizację w tej sekcji.

Należy wpisać kod między dwoma pragm, jak pokazano poniżej:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Programowanie rozwiązań

Podczas kompilowania kodu za pomocą optymalizacji można zauważyć dodatkowych komunikatów ostrzegawczych. To zachowanie jest oczekiwane, ponieważ pewne ostrzeżenia dotyczą tylko w zoptymalizowanym kodzie. Można uniknąć wiele problemów z optymalizacją, jeżeli uwzględnianie tych ostrzeżeń.

Paradoxically optymalizacji programu dla danej szybkości spowodować wolniejsze działanie kodu. Jest tak, ponieważ niektóre optymalizacje dla danej szybkości zwiększyć rozmiar kodu. Na przykład ze śródwierszowaniem funkcji eliminuje obciążenie wywołania funkcji. Jednakże wbudowanie zbyt dużej ilości kodu wprowadzać program tak duża, że numer strony pamięci wirtualnej błędów rośnie. W związku z tym szybkość, z wyeliminowanie wywołania funkcji, mogą zostać utracone na zamianę pamięci.

W poniższych tematach omówiono dobrych praktyk programowania.

[Wskazówki dotyczące poprawiania kodu wrażliwego na czas](tips-for-improving-time-critical-code.md) \
Lepiej techniki tworzenia kodu może zapewnić lepszą wydajność. W tym temacie sugeruje kodowania technik, które pomogą Ci upewnić się, czy pomyślnie wykonać czas ma istotne znaczenie fragmenty kodu.

[Najlepsze rozwiązania dotyczące optymalizacji](optimization-best-practices.md) \
Zawiera ogólne wytyczne dotyczące najlepszy sposób optymalizacji aplikacji.

## <a name="debugging-optimized-code"></a>Debugowanie zoptymalizowanego kodu

Ponieważ optymalizacji mogą ulec zmianie w kodzie, który został utworzony przez kompilator, firma Microsoft zaleca debugowania aplikacji i zmierzyć jej wydajność i następnie optymalizacji kodu.

Poniższe tematy zawierają informacje o tym, jak można debugować wersji kompilacji.

- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Instrukcje: Debugowanie zoptymalizowanego kodu](/visualstudio/debugger/how-to-debug-optimized-code)

- [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](why-floating-point-numbers-may-lose-precision.md)


Poniższe tematy zawierają informacje o tym, jak zoptymalizować kompilowania, ładowanie i wykonywanie kodu.

- [Poprawianie wydajności kompilatora](improving-compiler-throughput.md)

- [Korzystanie z nazwy funkcji bez () nie tworzy kodu](using-function-name-without-parens-produces-no-code.md)

- [Optymalizacja wbudowanego asemblera](../assembler/inline/optimizing-inline-assembly.md)

- [Określanie optymalizacji kompilatora dla projektu ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Jakich technik optymalizacji należy używać, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>W tej sekcji

[Optymalizacja Pragm i słów kluczowych](optimization-pragmas-and-keywords.md) \
[Poprawianie wydajności kompilatora](improving-compiler-throughput.md) \
[Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](why-floating-point-numbers-may-lose-precision.md) \
[Odwzorowanie liczby zmiennoprzecinkowej IEEE](ieee-floating-point-representation.md) \
[Wskazówki dotyczące poprawiania kodu wrażliwego na czas](tips-for-improving-time-critical-code.md) \
[Korzystanie z nazwy funkcji bez () nie tworzy kodu](using-function-name-without-parens-produces-no-code.md) \
[Najlepsze rozwiązania dotyczące optymalizacji](optimization-best-practices.md) \
[Optymalizacje sterowane profilem](profile-guided-optimizations.md) \
[Zmienne środowiskowe dla optymalizacji sterowanych profilem](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Instrukcje: Scalanie wielu profilów PGO w jeden profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](reference/c-cpp-building-reference.md)
