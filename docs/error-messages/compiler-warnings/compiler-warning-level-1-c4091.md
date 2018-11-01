---
title: Kompilator ostrzeżenie (poziom 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 87432a74dfe7c09a52f436d4e91b3f70eb66856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491744"
---
# <a name="compiler-warning-level-1-c4091"></a>Kompilator ostrzeżenie (poziom 1) C4091

"— słowo kluczowe": zignorowano na lewo od "type", gdy brak deklaracji zmiennej

Kompilator wykrył sytuacji, gdy użytkownik prawdopodobnie ma można zadeklarować zmienną, ale kompilator nie może zadeklarować zmienną.

## <a name="example"></a>Przykład

A `__declspec` atrybut znajdujący się na początku deklaracji typu zdefiniowanego przez użytkownika stosuje się do zmiennej tego typu. C4091 wskazuje, że brak deklaracji zmiennej. Poniższy przykład spowoduje wygenerowanie C4091.

```
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>Przykład

Identyfikator przypadku typedef nie może być również nazwa zmiennej. Poniższy przykład spowoduje wygenerowanie C4091.

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```