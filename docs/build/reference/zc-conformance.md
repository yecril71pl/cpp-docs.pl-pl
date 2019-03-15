---
title: /Zc (Zgodność)
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: e24dd53f9c805f57ce974a81a4963434f1868095
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821212"
---
# <a name="zc-conformance"></a>/Zc (Zgodność)

Możesz użyć **/Zc** opcji kompilatora, aby określić zachowanie kompilatora standardowe lub specyficzne dla firmy Microsoft.

## <a name="syntax"></a>Składnia

> **/ Zc:**_opcji_{,_opcji_}

## <a name="remarks"></a>Uwagi

W przypadku wdrożenia programu Visual Studio rozszerzenia C lub C++, który nie jest zgodny ze standardem można użyć `/Zc` opcję zgodności, aby określić zachowanie zgodne standardowe lub specyficzne dla firmy Microsoft. Niektóre opcje zachowania specyficzne dla firmy Microsoft jest zachowaniem domyślnym, aby uniemożliwić na dużą skalę przełomowe zmiany do istniejącego kodu. W innych przypadkach wartość domyślna to standardowe zachowanie, gdzie poprawę zabezpieczeń, wydajności i zgodności przeważają koszty istotne zmiany. Domyślne ustawienie każdej opcji zgodności mogą ulec zmianie w nowszej wersji programu Visual Studio. Aby uzyskać więcej informacji na temat poszczególnych opcji zgodności zobacz temat dla określonych opcji. [/ Permissive-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia opcje zgodności, które nie są ustawione, aby domyślnie ich ustawień zgodności.

Są to `/Zc` opcje kompilatora:

|Opcja|Zachowanie|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Włącz C ++ 17 nadmiernie wyrównanych dynamicznej alokacji (domyślnie włączone w języku C ++ 17).|
|[auto\[-\]](zc-auto-deduce-variable-type.md)|Wymuszaj nowe znaczenie standardu C++ dla `auto` (w domyślnym).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Włącz **__cplusplus** makra, aby zgłosić obsługiwanych standard (funkcja domyślnie wyłączona).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Włącz połączenie zewnętrzne dla `constexpr` zmienne (funkcja domyślnie wyłączona).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Wymuszaj Standard C++ `for` reguł ustawiania zakresu (w domyślnym).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Włącz niejawny `noexcept` dla funkcji wymagana (w domyślnym).|
|[inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|Usuń nieużywane funkcję lub dane, jeśli to sekcja COMDAT lub zawierają tylko powiązanie wewnętrzne (funkcja domyślnie wyłączona).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Wymuszanie reguł 17 noexcept języka C ++ (na domyślnie w języku C ++ 17 lub nowszej).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Tymczasowe UDT nie zostanie powiązana z odwołaniem lvalue niestały (funkcja domyślnie wyłączona).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Wymuszanie zasad konwersji typów jawnych standardowego języka C++ (funkcja domyślnie wyłączona).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Włączanie funkcji 14 globalnego dezalokacji o rozmiarze C ++ (w domyślnym).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Wyłącz literału ciągu do `char*` lub `wchar_t*` konwersji (funkcja domyślnie wyłączona).|
|[trójargumentowy\[-\]](zc-ternary.md)|Wymuszanie reguł operatora warunkowego na typy argumentów operacji (funkcja domyślnie wyłączona).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Włącz wątkowo lokalne statyczne inicjowanie (w domyślnym).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Załóżmy `operator new` zgłoszenie błędu (funkcja domyślnie wyłączona).|
|[Trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|Włącz trigraphs (przestarzałe, wyłącz domyślnie).|
|[twoPhase-](zc-twophase.md)|Szablon niezgodnych analizy zachowania, które (zgodnie z domyślnym).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` jest typem natywnym, nie element typedef (w domyślnym).|

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
