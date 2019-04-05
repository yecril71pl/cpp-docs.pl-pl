---
title: '#Dyrektywy ifdef i #ifndef (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: d7a6a1604df03f0607f33e42880270cbdcd62e8b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027233"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>Dyrektywy #ifdef i #ifndef (C/C++)
**#Ifdef** i **#ifndef** dyrektywy wykonują to samo zadanie jako `#if` dyrektywy, gdy jest używany z **zdefiniowane**( *identyfikator* ).

## <a name="syntax"></a>Składnia

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>Uwagi

Możesz użyć **#ifdef** i **#ifndef** dyrektywy w dowolnym miejscu `#if` mogą być używane. **#Ifdef** *identyfikator* instrukcja jest odpowiednikiem `#if 1` podczas *identyfikator* została zdefiniowana, a odpowiada `#if 0` podczas *identyfikator* nie został zdefiniowany lub jego definicja została usunięta z `#undef` dyrektywy. Te dyrektywy sprawdzić jedynie obecność lub brak obecności identyfikatorów zdefiniowanych z `#define`, a nie identyfikatorów zdeklarowanych w kodzie źródłowym C lub C++.

Te dyrektywy są uwzględnione jedynie w celu zgodności z poprzednimi wersjami języka. **Zdefiniowane (** *identyfikator* **)** wyrażenia stałego używanego z `#if` dyrektywą.

**#Ifndef** dyrektywy sprawdza przeciwieństwo warunku sprawdzone przez **#ifdef**. Jeśli nie zdefiniowano identyfikatora (lub jego definicja została usunięta z `#undef`), warunek ma wartość true (niezerową). W przeciwnym razie warunek jest fałszywy (0).

**Specyficzne dla firmy Microsoft**

*Identyfikator* może być przekazywany z wiersza polecenia przy użyciu `/D` opcji. Do 30 makr można określić za pomocą `/D`.

Jest to przydatne w przypadku sprawdzania, czy definicja istnieje, ponieważ definicja może być przekazana z wiersza polecenia. Na przykład:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)