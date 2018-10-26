---
title: '#Dyrektywy ifdef i #ifndef (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1ba603941b5d08bc56d8385f2b721fb1bef6586
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075895"
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

**Microsoft Specific**

*Identyfikator* może być przekazywany z wiersza polecenia przy użyciu `/D` opcji. Do 30 makr można określić za pomocą `/D`.

Jest to przydatne w przypadku sprawdzania, czy definicja istnieje, ponieważ definicja może być przekazana z wiersza polecenia. Na przykład:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)