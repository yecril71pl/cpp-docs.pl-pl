---
title: Błąd kompilatora C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: d761dfde26cce9c99ccd4c3e6fd86ae1d6e16ddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351095"
---
# <a name="compiler-error-c2015"></a>Błąd kompilatora C2015

za dużo znaków w stałej

Stałej znakowej zawiera więcej niż dwa znaki. Limit wynosi jeden znak dla stałych znaków standardowych i dwa znaki dla stałych znaków długie.

Sekwencja wyjścia, takich jak \t, jest konwertowany na pojedynczy znak.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2015:

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Przykład

C2015 może również wystąpić w przypadku korzystania z rozszerzeniem firmy Microsoft, stałe znaków konwertowane na liczby całkowite.  Poniższy przykład spowoduje wygenerowanie C2015:

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```