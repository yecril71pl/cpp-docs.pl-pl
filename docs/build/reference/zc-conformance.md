---
title: "-Zc-(zgodność) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zc
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8c959926cd1ae15ebc8087a9dc3237fdeeb34fa8
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="zc-conformance"></a>/Zc (Zgodność)

Można użyć **/Zc** opcji kompilatora, aby określić zachowanie kompilatora standard lub specyficzne dla firmy Microsoft.

## <a name="syntax"></a>Składnia

> / Zc:_opcji_{,_opcji_}

## <a name="remarks"></a>Uwagi

Po zaimplementowaniu rozszerzenia do C lub C++, która nie jest zgodna ze standardem Visual Studio można używać `/Zc` zgodność opcję, aby określić zachowanie zgodnych standard lub specyficzne dla firmy Microsoft. W przypadku niektórych opcji zachowanie specyficzne dla firmy Microsoft jest domyślne, aby uniemożliwić podziału na dużą skalę zmiany istniejącego kodu. W pozostałych przypadkach wartość domyślna to standardowe zachowanie, w których ulepszenia zabezpieczeń, wydajności i zgodności mają większe niż koszty fundamentalne zmiany. Ustawieniem domyślnym każdej opcji zgodności mogą ulec zmianie w nowszych wersjach programu Visual Studio. Aby uzyskać więcej informacji na temat poszczególnych opcji zgodności zobacz temat dla określonych opcji.

Są to `/Zc` — opcje kompilatora:

|Opcja|Zachowanie|
|---|---|
|[Automatycznie\[-\]](zc-auto-deduce-variable-type.md)|Wymuszaj nowe znaczenie standardu C++ dla `auto` (na domyślnie).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Włącz połączenie zewnętrzne dla `constexpr` zmienne (domyślnie wyłączone).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Wymuszaj Standard C++ `for` reguł ustawiania zakresu (na domyślnie).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Włącz niejawny `noexcept` dla funkcji wymaganych (na domyślnie).|
|[wbudowany\[-\]](zc-inline-remove-unreferenced-comdat.md)|Usuń nieużywane funkcję lub dane, jeśli jest COMDAT lub zawierają tylko powiązanie wewnętrzne (domyślnie wyłączone).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Wymuś reguły 17 noexcept C ++ (na domyślnie w języku C ++ 17 lub nowszej).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Tymczasowe UDT nie zostanie powiązana z odwołania do wartości innej niż stała (domyślnie wyłączone).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Wymuś reguły konwersji typu jawnego Standard C++ (domyślnie wyłączone).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Włącz funkcje 14 globalnego cofania alokacji o rozmiarze C ++ (na domyślnie).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Wyłącz literał ciągu do `char*` lub `wchar_t*` konwersji (domyślnie wyłączone).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Włącz wątkowo lokalnego Inicjowanie statyczne (w domyślnym).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Załóżmy `operator new` zgłoszenie błędu (domyślnie wyłączone).|
|[trigramów\[-\]](zc-trigraphs-trigraphs-substitution.md)|Włącz trigramów (przestarzałe, wyłącz domyślnie).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t`jest typem natywnym, a nie typem typedef (na domyślnie).|

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](compiler-options.md)  
[Ustawianie opcji kompilatora](setting-compiler-options.md)
