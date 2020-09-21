---
title: Błąd kompilatora C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 5453009e1c2bd091ed3507f3c43bd7fcecd33abc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743103"
---
# <a name="compiler-error-c2015"></a>Błąd kompilatora C2015

zbyt wiele znaków w stałej

Stała znakowa zawiera więcej niż dwa znaki. Limit jest jednym znakiem dla stałych znaków standardowych i dwóch znaków dla stałych znaków długich.

Sekwencja ucieczki, taka jak \t, jest konwertowana na pojedynczy znak.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2015:

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

C2015 może również wystąpić w przypadku korzystania z rozszerzenia Microsoft, stałe znakowe konwertowane na liczby całkowite.  Poniższy przykład generuje C2015:

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
