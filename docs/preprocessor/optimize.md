---
title: optimize, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220519"
---
# <a name="optimize-pragma"></a>optimize, pragma

Określa optymalizacje na zasadzie funkcji przez funkcję.

## <a name="syntax"></a>Składnia

> **#pragma Optymalizuj ("** [ *Lista optymalizacji* ] **",** { **on** | **off** } **)**

## <a name="remarks"></a>Uwagi

**Optymalizacja** pragma musi znajdować się poza funkcją. Zacznie obowiązywać przy pierwszej funkcji zdefiniowanej po wystąpieniu dyrektywy pragma. Argumenty **włączone** i **wyłączone** włączają opcje określone na *liście Optymalizacja —* włączone lub wyłączone.

*Lista optymalizacji* może być równa zero lub więcej parametrów przedstawionych w poniższej tabeli.

### <a name="parameters-of-the-optimize-pragma"></a>Parametry optymalizacji dyrektywy pragma

| Parametry | Typ optymalizacji |
|--------------------|--------------------------|
| **g** | Włącz optymalizacje globalne. |
| **s** lub **t** | Określ krótkie lub szybkie sekwencje kodu maszynowego. |
| **y** | Generuj wskaźniki ramek na stosie programów. |

Te parametry są te same litery, które są używane z opcjami kompilatora [/o](../build/reference/o-options-optimize-code.md) . Na przykład następująca pragma jest równoważna `/Os` z opcją kompilatora:

```cpp
#pragma optimize( "s", on )
```

Używanie **optymalizacji** dyrektywy pragma z pustym ciągiem ( **""** ) jest specjalną formą dyrektywy:

Użycie parametru **off** powoduje włączenie wszystkich optymalizacji, **g**, **s**, **t**i **y**.

**W** przypadku użycia parametru on resetuje optymalizacje do tych, które zostały określone przy użyciu opcji " [/o](../build/reference/o-options-optimize-code.md) kompilatora".

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
