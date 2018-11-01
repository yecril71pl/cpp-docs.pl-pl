---
title: Błąd kompilatora C2009
ms.date: 11/04/2016
f1_keywords:
- C2009
helpviewer_keywords:
- C2009
ms.assetid: fe9d94ed-20a5-4d83-b9c4-60ee69d2f30a
ms.openlocfilehash: d2216b3fe990109828492fb2b2055e9425c1e306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638779"
---
# <a name="compiler-error-c2009"></a>Błąd kompilatora C2009

ponowne użycie formalne makra 'Identyfikator'

Listy parametrów formalnych w definicji makra używa identyfikatora więcej niż jeden raz. Identyfikatory w liście parametrów makra muszą być unikatowe.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2009:

```
// C2009.cpp
#include <stdio.h>

#define macro1(a,a) (a*a)   // C2009

int main()
{
    printf_s("%d\n", macro1(2));
}
```

## <a name="example"></a>Przykład

Możliwe rozwiązanie:

```
// C2009b.cpp
#include <stdio.h>

#define macro2(a)   (a*a)
#define macro3(a,b) (a*b)

int main()
{
    printf_s("%d\n", macro2(2));
    printf_s("%d\n", macro3(2,4));
}
```