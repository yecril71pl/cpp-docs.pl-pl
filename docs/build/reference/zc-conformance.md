---
title: /Zc (Zgodność)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6d6d3b7736fd1775372a3b2093c53e177db5099e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234357"
---
# <a name="zc-conformance"></a>`/Zc`Zgodności

Możesz użyć **`/Zc`** opcji kompilatora, aby określić zachowanie kompilatora standardowego lub określonego przez firmę Microsoft.

## <a name="syntax"></a>Składnia

> **`/Zc:`**_opcja_{,_Option_}

## <a name="remarks"></a>Uwagi

Gdy program Visual Studio zaimplementował rozszerzenie w języku C lub C++, które nie jest zgodne ze standardem, można użyć **`/Zc`** opcji zgodności, aby określić zachowanie zgodne ze standardem lub specyficznym dla firmy Microsoft. W przypadku niektórych opcji zachowanie specyficzne dla firmy Microsoft jest domyślne, aby zapobiec zmianom w dużej skali w istniejącym kodzie. W innych przypadkach ustawieniem domyślnym jest standardowe zachowanie, w którym ulepszenia zabezpieczeń, wydajności i zgodności zwiększają koszty związane z istotnymi zmianami. Ustawienie domyślne każdej opcji zgodności może ulec zmianie w nowszych wersjach programu Visual Studio. Więcej informacji o każdej opcji zgodności można znaleźć w temacie dotyczącym konkretnej opcji. [`/permissive-`](permissive-standards-conformance.md)Opcja kompilatora niejawnie ustawia opcje zgodności, które nie są domyślnie ustawione jako zgodne z ustawieniem zgodnym.

Są to **`/Zc`** Opcje kompilatora:

| Opcja | Zachowanie |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | Włącz alokację dynamiczną w języku C++ 17 (domyślnie włączona w języku C++ 17). |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | Wymuś nowe standardowe znaczenie języka C++ **`auto`** (domyślnie włączone). |
| [`/Zc__cplusplus`](zc-cplusplus.md) | Zezwól `__cplusplus` makro na raportowanie obsługiwanego standardu (domyślnie wyłączone). |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | Włącz zewnętrzne powiązanie dla **`constexpr`** zmiennych (domyślnie wyłączone). |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | Wymuszaj standardowe **`for`** reguły określania zakresu C++ (domyślnie włączone). |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | Włącz niejawne **`noexcept`** dla wymaganych funkcji (domyślnie włączone). |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | Usuń odwołującą się funkcję lub dane, jeśli jest COMDAT lub ma tylko wewnętrzne połączenie (domyślnie wyłączone). |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | Wymuś reguły języka C++ 17 **`noexcept`** (włączone domyślnie w języku c++ 17 lub nowszym). |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | Tymczasowa wartość parametru UDT nie zostanie powiązana z odwołaniem lvalue innym niż const (domyślnie wyłączone). |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | Wymuszaj reguły konwersji jawnego typu standardowego języka C++ (domyślnie wyłączone). |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | Włącz funkcje cofania alokacji o rozmiarze globalnym w języku C++ 14 (domyślnie włączone). |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | Wyłączenie lub konwersja literału ciągu znaków `char*` `wchar_t*` (domyślnie wyłączone). |
| [`/Zc:ternary`](zc-ternary.md) | Wymuszaj reguły operatora warunkowego dla typów operandów (domyślnie wyłączone). |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | Włącz bezpieczne statyczne inicjalizacje lokalne w wątkach (domyślnie włączone). |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | Załóżmy **`operator new`** , że w przypadku niepowodzenia (domyślnie jest to wyłączone). |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | Włącz trigraphs (przestarzałe, domyślnie wyłączone). |
| [`/Zc:twoPhase`](zc-twophase.md) | Użyj zachowania niezgodnego z analizą szablonu (domyślnie zgodne). |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** jest typem natywnym, a nie elementem TypeDef (domyślnie włączonym). |

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
