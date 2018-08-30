---
title: Specyfikatory typu C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f965481ae1d3abea40577680b1af72004f793123
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197231"
---
# <a name="c-type-specifiers"></a>Specyfikatory typu C

Specyfikatory typów w deklaracjach zdefiniować typu w deklaracji zmiennej lub funkcji.

## <a name="syntax"></a>Składnia

*Specyfikator typu*:  
&nbsp;&nbsp;**Void**  
&nbsp;&nbsp;**Char**  
&nbsp;&nbsp;**Krótka**  
&nbsp;&nbsp;**int**  
&nbsp;&nbsp;**długi**  
&nbsp;&nbsp;**float**  
&nbsp;&nbsp;**Podwójne**  
&nbsp;&nbsp;**Podpisany**  
&nbsp;&nbsp;**Bez znaku**  
&nbsp;&nbsp;*struct-or-union-specifier*  
&nbsp;&nbsp;*enum-specifier*  
&nbsp;&nbsp;*Nazwa TypeDef*  

**Podpisany char**, **podpisany int**, **podpisany krótka wartość całkowita**, i **podpisany long int** typów, wraz z ich **bez znaku**  odpowiedniki i **wyliczenia**, są nazywane *całkowitego* typów. **Float**, **double**, i **typu long double** specyfikatory typu są określane jako *zmiennoprzecinkowy* lub *zmiennoprzecinkowych* typów. W deklaracji zmiennej lub funkcji, można użyć dowolnego Specyfikator typu całkowitego lub zmiennoprzecinkowego. Jeśli *Specyfikator typu* nie znajduje się w deklaracji, jest traktowana jako **int**.

Opcjonalne słowa kluczowe **podpisany** i **niepodpisane** może poprzedzać lub skorzystać z dowolnego typu całkowitoliczbowego z wyjątkiem **wyliczenia**i może również służyć jako specyfikatory typu, w którym to przypadku Rozumiemy jako **podpisany int** i **unsigned int**odpowiednio. Gdy jest używana samodzielnie, słowo kluczowe **int** zakłada się, że **podpisany**. Gdy jest używana samodzielnie, słowa kluczowe **długie** i **krótki** są zrozumiałe jako **long int** i **krótka wartość całkowita**.

Typy wyliczeniowe są traktowane jako typy podstawowe. Specyfikatory typu dla typów wyliczenia zostały omówione w [deklaracje modułów Wyliczających](../c-language/c-enumeration-declarations.md).

Słowo kluczowe **void** ma trzy zastosowań: Aby określić funkcję zwracany typ, aby określić listy Typ argumentu dla funkcji, która nie przyjmuje żadnych argumentów, a także do określenia wskaźnika do nieokreślonego typu. Możesz użyć **void** typu, Zadeklaruj funkcje wracające żadnej wartości lub zadeklarować wskaźnika do nieokreślonego typu. Zobacz [argumenty](../c-language/arguments.md) uzyskać informacji na temat **void** , gdy pojawia się tylko w obrębie nawiasów po nazwie funkcji.

**Microsoft Specific**

Kontrola typów jest teraz ze standardem ANSI, co oznacza, że typ **krótki** i typ **int** są różnych typów. Na przykład to dokonanym w kompilatorze Microsoft C, który został zaakceptowany przez poprzednie wersje kompilatora.

```C
int   myfunc();
short myfunc();
```

Ten przykład dalej również generuje ostrzeżenie dotyczące operatora pośredniego do różnych typów:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilator Microsoft C: generuje również wyświetlanie ostrzeżeń dotyczących różnice w logowania. Na przykład:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Typ **void** wyrażenia są obliczane na efektów ubocznych. Nie można używać (nieistniejącej) wartości wyrażenia typu **void** w dowolnym sposób ani może konwersji **void** wyrażenia (przez jawnych lub niejawnych konwersji) do dowolnego typu z wyjątkiem **void** . Jeśli używasz innego typu wyrażenia w kontekście gdzie **void** wyrażenie jest wymagany, jego wartość jest odrzucany.

Aby były zgodne ze specyfikacją ANSI <strong>void\* \*</strong>  nie można użyć jako <strong>int\*\*</strong>. Tylko **void** <strong>\*</strong> może służyć jako wskaźnik do nieokreślonego typu.

**END specyficzny dla Microsoft**

Można utworzyć dodatkowy typ specyfikatory z **typedef** deklaracji, zgodnie z opisem w [deklaracje Typedef](../c-language/typedef-declarations.md). Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji na podstawie rozmiaru każdego typu.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)  
