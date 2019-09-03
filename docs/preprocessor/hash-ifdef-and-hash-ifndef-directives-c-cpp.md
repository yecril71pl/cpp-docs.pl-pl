---
title: '#ifdef i #ifndef, dyrektywy (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220112"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>dyrektywy #ifdef i #ifndef (C/C++)

Dyrektywy **#ifdef** i **#ifndef** mają taki sam skutek jak dyrektywa [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) , gdy jest ona używana ze zdefiniowanym operatorem.

## <a name="syntax"></a>Składnia

> **#ifdef** *Identyfikator*\
> **#ifndef** *Identyfikator*

Dyrektywy te są równoważne:

> **zdefiniowano #if** *Identyfikator*\
> **#if! zdefiniowane** *Identyfikator*

## <a name="remarks"></a>Uwagi

Możesz użyć dyrektyw **#ifdef** i **#ifndef** w dowolnym miejscu `#if` . Instrukcja **#ifdef** *Identifier* jest równoznaczna z `#if 1` , gdy zdefiniowano *Identyfikator* . Jest równoważne `#if 0` , gdy *Identyfikator* nie został zdefiniowany lub został niezdefiniowany przez `#undef` dyrektywę. Te dyrektywy sprawdzają tylko obecność lub brak identyfikatorów zdefiniowanych przy użyciu `#define`, a nie dla identyfikatorów zadeklarowanych w kodzie C lub C++ źródłowym.

Dyrektywy te są dostępne tylko w celu zapewnienia zgodności z poprzednimi wersjami tego języka. Preferowane wyrażenie`#if` stałej (Identifier) używane z dyrektywą jest zalecane.

Dyrektywa **#ifndef** sprawdza przeciwieństwo warunku sprawdzonego przez **#ifdef**. Jeśli identyfikator nie został zdefiniowany lub jeśli jego definicja została usunięta z `#undef`, warunek ma wartość true (niezerowa). W przeciwnym razie warunek ma wartość false (0).

**Microsoft Specific**

*Identyfikator* można przesłać z wiersza polecenia przy użyciu [/d](../build/reference/d-preprocessor-definitions.md) opcji. Do 30 makr można określić za pomocą `/D`.

Dyrektywa **#ifdef** jest przydatna do sprawdzania, czy definicja istnieje, ponieważ definicja może być przenoszona z wiersza polecenia. Na przykład:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
