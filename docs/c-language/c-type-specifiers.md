---
title: Specyfikatory typu C | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00d91c2f790b93e70f21557d85f2cbb8216c8ed3
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="c-type-specifiers"></a>Specyfikatory typu C

Specyfikatory typów w deklaracjach typ deklaracji zmiennej lub funkcji.

## <a name="syntax"></a>Składnia

*Specyfikator typu*:  
&nbsp;&nbsp;**Void**  
&nbsp;&nbsp;**char**  
&nbsp;&nbsp;**krótki**  
&nbsp;&nbsp;**int**  
&nbsp;&nbsp;**długa**  
&nbsp;&nbsp;**Float**  
&nbsp;&nbsp;**O podwójnej precyzji**  
&nbsp;&nbsp;**Podpisany**  
&nbsp;&nbsp;**Bez znaku**  
&nbsp;&nbsp;*struct-or-union-specifier*  
&nbsp;&nbsp;*enum-specifier*  
&nbsp;&nbsp;*Nazwa typu TypeDef*  

**Podpisany char**, **podpisany int**, **podpisany krótkich liczb całkowitych**, i **podpisany długi int** typów, wraz z ich **bez znaku**  odpowiednikowi i **wyliczenia**, są nazywane *integralną* typów. **Float**, **podwójne**, i **podwójnej długości** specyfikatorze typu są określane jako *przestawne* lub *liczbzmiennoprzecinkowych* typów. W deklaracji zmiennej lub funkcji, można użyć dowolnego specyfikatora typu całkowitego lub zmiennoprzecinkowej. Jeśli *specyfikatora typu* nie jest dostępny w deklaracji, przyjmuje się **int**.

Opcjonalne słowa kluczowe **podpisany** i **niepodpisane** może poprzedzać lub skorzystać z dowolnego z typów całkowitych z wyjątkiem **wyliczenia**i może również służyć jako specyfikatorze typu, w którym to przypadku rozumie jako **podpisany int** i **unsigned int**odpowiednio. Gdy użyte bez parametrów, słowo kluczowe **int** zakłada się, że **podpisany**. Gdy użyte bez parametrów, słowa kluczowe **długi** i **krótki** rozumie jako **długi int** i **krótkich liczb całkowitych**.

Typy wyliczeniowe są traktowane jako typów podstawowych. Specyfikatory typów dla typów wyliczenia, omówiono w [deklaracje modułów Wyliczających](../c-language/c-enumeration-declarations.md).

Słowo kluczowe **void** ma trzy zastosowań: Aby określić funkcję zwracany typ, aby określić listę typ argumentu dla funkcji, która nie przyjmuje żadnych argumentów i określić wskaźnik do nieokreślonego typu. Można użyć **void** typu do zadeklarowania funkcji zwracających wartości lub zadeklarować wskaźnika nieokreślonego typu. Zobacz [argumenty](../c-language/arguments.md) uzyskać informacji o **void** po wyświetleniu wyłącznie wewnątrz nawiasów po nazwie funkcji.

**Microsoft Specific**

Sprawdzanie typu jest teraz ANSI zgodne, co oznacza, że typ **krótki** i typ **int** są różne typy. Na przykład jest to ponowna definicja w kompilatorze C firmy Microsoft, który został zaakceptowany przez poprzednie wersje kompilatora.

```C
int   myfunc();
short myfunc();
```

W tym przykładzie dalej również generuje ostrzeżenie o pośredni do różnych typów:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilator Microsoft C generuje również ostrzeżeń dotyczących różnic w logowania. Na przykład:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Typ **void** wyrażenia są oceniane pod kątem efekty uboczne. Nie można użyć (nieistniejącą) wartości wyrażenia o typie **void** w dowolnym sposób ani może konwersji **void** wyrażenia (za pomocą konwersji jawnych ani niejawnych) do dowolnego typu, z wyjątkiem **void** . Użycie innego typu wyrażenia w kontekście, w którym **void** wymagane jest wyrażenie, jego wartość jest usuwana.

Aby był zgodny ze specyfikacją ANSI **void\* \***  nie można użyć jako **int\*\***. Tylko **void\***  może być używany jako wskaźnik do nieokreślonego typu.

**KOŃCOWY określonych firmy Microsoft**

Możesz utworzyć dodatkowe typu specyfikatory z **typedef** deklaracje, zgodnie z opisem w [deklaracje Typedef](../c-language/typedef-declarations.md). Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji na temat rozmiar każdego typu.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)  
