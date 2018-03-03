---
title: "-Zc-(zgodność) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zc
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba64cf2e866579b3377e57445c98eb9a436a1edd
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
|[alignedNew\[-\]](zc-alignednew.md)|Włączanie języka C ++ 17 nadmiernie wyrównany dynamicznej alokacji (domyślnie włączone w języku C ++ 17).|
|[auto\[-\]](zc-auto-deduce-variable-type.md)|Wymuszaj nowe znaczenie standardu C++ dla `auto` (na domyślnie).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Włącz połączenie zewnętrzne dla `constexpr` zmienne (domyślnie wyłączone).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Wymuszaj Standard C++ `for` reguł ustawiania zakresu (na domyślnie).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Włącz niejawny `noexcept` dla funkcji wymaganych (na domyślnie).|
|[inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|Usuń nieużywane funkcję lub dane, jeśli jest COMDAT lub zawierają tylko powiązanie wewnętrzne (domyślnie wyłączone).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Wymuś reguły 17 noexcept C ++ (na domyślnie w języku C ++ 17 lub nowszej).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Tymczasowe UDT nie zostanie powiązana z odwołania do wartości innej niż stała (domyślnie wyłączone).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Wymuś reguły konwersji typu jawnego Standard C++ (domyślnie wyłączone).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Włącz funkcje 14 globalnego cofania alokacji o rozmiarze C ++ (na domyślnie).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Wyłącz literał ciągu do `char*` lub `wchar_t*` konwersji (domyślnie wyłączone).|
|[trzyargumentowe\[-\]](zc-ternary.md)|Operator warunkowy zasady na typy argumentów operacji (domyślnie wyłączone).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Włącz wątkowo lokalnego Inicjowanie statyczne (w domyślnym).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Załóżmy `operator new` zgłoszenie błędu (domyślnie wyłączone).|
|[trigramów\[-\]](zc-trigraphs-trigraphs-substitution.md)|Włącz trigramów (przestarzałe, wyłącz domyślnie).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t`jest typem natywnym, a nie typem typedef (na domyślnie).|

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](compiler-options.md)  
[Ustawianie opcji kompilatora](setting-compiler-options.md)
