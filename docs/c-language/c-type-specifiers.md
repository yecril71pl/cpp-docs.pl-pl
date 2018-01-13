---
title: Specyfikatory typu C | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28712275312bf653e082a9f8e32424f26534fb93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-type-specifiers"></a>Specyfikatory typu C
Specyfikatory typów w deklaracjach typ deklaracji zmiennej lub funkcji.  
  
## <a name="syntax"></a>Składnia  
 *Specyfikator typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **podpisany**  
  
 **bez znaku**  
  
 *Specyfikator Struct lub union*  
  
 *Enum — Specyfikator*  
  
 *Nazwa typu TypeDef*  
  
 **Podpisany char**, **podpisany int**, **podpisany krótkich liczb całkowitych**, i **podpisany długi int** typów, wraz z ich `unsigned` odpowiednikami i `enum`, są nazywane typy "zintegrowane". **Float**, **podwójne**, i `long double` specyfikatorze typu są określane jako "przestawne" lub "zmiennoprzecinkowe" typów. W deklaracji zmiennej lub funkcji, można użyć dowolnego specyfikatora typu całkowitego lub zmiennoprzecinkowej. Jeśli *specyfikatora typu* nie jest dostępny w deklaracji, przyjmuje się `int`.  
  
 Opcjonalne słowa kluczowe **podpisany** i `unsigned` może poprzedzać lub skorzystać z dowolnego z typów całkowitych z wyjątkiem `enum`i może również służyć wyłącznie jako specyfikatorze typu, w którym to przypadku one są rozumiana jako **podpisany int**  i `unsigned int`odpowiednio. Gdy użyte bez parametrów, słowo kluczowe `int` zakłada się, że **podpisany**. Gdy użyte bez parametrów, słowa kluczowe **długi** i **krótki** rozumie jako **długi int** i `short int`.  
  
 Typy wyliczeniowe są traktowane jako typów podstawowych. Specyfikatory typów dla typów wyliczenia, omówiono w [deklaracje modułów Wyliczających](../c-language/c-enumeration-declarations.md).  
  
 Słowo kluczowe `void` ma trzy zastosowań: Aby określić funkcję zwracany typ, aby określić listę typ argumentu dla funkcji, która nie przyjmuje żadnych argumentów i określić wskaźnik do nieokreślonego typu. Można użyć `void` typu do zadeklarowania funkcji zwracających wartości lub zadeklarować wskaźnika nieokreślonego typu. Zobacz [argumenty](../c-language/arguments.md) uzyskać informacji o `void` po wyświetleniu wyłącznie wewnątrz nawiasów po nazwie funkcji.  
  
 **Dotyczące firmy Microsoft**  
  
 Sprawdzanie typu jest teraz ANSI zgodne, co oznacza, że typ **krótki** i typu `int` są różne typy. Na przykład jest to ponowna definicja w kompilatorze C firmy Microsoft, który został zaakceptowany przez poprzednie wersje kompilatora.  
  
```  
int   myfunc();  
short myfunc();  
```  
  
 W tym przykładzie dalej również generuje ostrzeżenie o pośredni do różnych typów:  
  
```  
int *pi;  
short *ps;  
  
ps = pi;  /* Now generates warning */  
```  
  
 Kompilator Microsoft C generuje również ostrzeżeń dotyczących różnic w logowania. Na przykład:  
  
```  
signed int *pi;  
unsigned int *pu  
  
pi = pu;  /* Now generates warning */  
```  
  
 Typ `void` wyrażenia są oceniane pod kątem efekty uboczne. Nie można użyć (nieistniejącą) wartości wyrażenia o typie `void` w dowolnym sposób ani może konwersji `void` wyrażenia (za pomocą konwersji jawnych ani niejawnych) do dowolnego typu, z wyjątkiem `void`. Użycie innego typu wyrażenia w kontekście, w którym `void` wymagane jest wyrażenie, jego wartość jest usuwana.  
  
 Aby był zgodny ze specyfikacją ANSI **void\* \***  nie można użyć jako **int\*\***. Tylko **void\***  może być używany jako wskaźnik do nieokreślonego typu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Możesz utworzyć dodatkowe typu specyfikatory z `typedef` deklaracje, zgodnie z opisem w [deklaracje Typedef](../c-language/typedef-declarations.md). Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji na temat rozmiar każdego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)