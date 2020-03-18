---
title: /Zc (Zgodność)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438671"
---
# <a name="zc-conformance"></a>/Zc (Zgodność)

Możesz użyć opcji kompilatora **/Zc** , aby określić zachowanie kompilatora standardowego lub określonego przez firmę Microsoft.

## <a name="syntax"></a>Składnia

> **/Zc:** _opcja_{,_Option_}

## <a name="remarks"></a>Uwagi

Gdy program Visual Studio zaimplementował rozszerzenie C lub C++ nie jest zgodne ze standardem, można użyć opcji zgodność `/Zc`, aby określić zachowanie zgodne ze standardem lub specyficznym dla firmy Microsoft. W przypadku niektórych opcji zachowanie specyficzne dla firmy Microsoft jest domyślne, aby zapobiec zmianom w dużej skali w istniejącym kodzie. W innych przypadkach ustawieniem domyślnym jest standardowe zachowanie, w którym ulepszenia zabezpieczeń, wydajności i zgodności zwiększają koszty związane z istotnymi zmianami. Ustawienie domyślne każdej opcji zgodności może ulec zmianie w nowszych wersjach programu Visual Studio. Więcej informacji o każdej opcji zgodności można znaleźć w temacie dotyczącym konkretnej opcji. Opcja kompilatora [/permissive-](permissive-standards-conformance.md) niejawnie ustawia opcje zgodności, które nie są domyślnie ustawiane jako ustawienia zgodne.

Oto opcje kompilatora `/Zc`:

|Opcja|Zachowanie|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Włącz alokację dynamiczną w języku C++ 17 (domyślnie włączona w języku C++ 17).|
|[\[-\]](zc-auto-deduce-variable-type.md)|Wymuś nowe standardowe C++ znaczenie dla `auto` (domyślnie włączone).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Zezwól makro **__cplusplus** na raportowanie obsługiwanego standardu (domyślnie wyłączone).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Włącz zewnętrzne powiązanie dla zmiennych `constexpr` (domyślnie wyłączone).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Wymuszaj standardowe C++ reguły określania zakresu `for` (domyślnie włączone).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Włącz niejawne `noexcept` w wymaganych funkcjach (domyślnie włączone).|
|[\[wbudowane -\]](zc-inline-remove-unreferenced-comdat.md)|Usuń odwołującą się funkcję lub dane, jeśli jest COMDAT lub ma tylko wewnętrzne połączenie (domyślnie wyłączone).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Wymuś reguły noexcept języka C++ 17 (włączone domyślnie w języku C++ 17 lub nowszym).|
|[referencebinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Tymczasowa wartość parametru UDT nie zostanie powiązana z odwołaniem lvalue innym niż const (domyślnie wyłączone).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Wymuszaj reguły C++ jawnej konwersji typu standardowego (domyślnie wyłączone).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Włącz funkcje cofania alokacji o rozmiarze globalnym w języku C++ 14 (domyślnie włączone).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Wyłącz konwersję ciągu literału na `char*` lub `wchar_t*` konwersji (domyślnie jest to wyłączone).|
|[\[Trzyelementowy -\]](zc-ternary.md)|Wymuszaj reguły operatora warunkowego dla typów operandów (domyślnie wyłączone).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Włącz bezpieczne statyczne inicjalizacje lokalne w wątkach (domyślnie włączone).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Załóżmy, że `operator new` zgłasza niepowodzenie (domyślnie wyłączone).|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|Włącz trigraphs (przestarzałe, domyślnie wyłączone).|
|[twoPhase](zc-twophase.md)|Użyj zachowania niezgodnego z analizą szablonu (domyślnie zgodne).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` jest typem natywnym, a nie elementem TypeDef (domyślnie włączonym).|

Aby uzyskać więcej informacji na temat problemów ze zgodnością C++w wizualizacji, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
