---
title: Błąd kompilatora C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 6b40a3bd186b5c45a0ea5163f433635ab1e7b07f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743493"
---
# <a name="compiler-error-c2001"></a>Błąd kompilatora C2001

stała nowego wiersza

Stała ciągu nie może być kontynuowana w drugim wierszu, chyba że wykonasz następujące czynności:

- Zakończ pierwszy wiersz za pomocą ukośnika odwrotnego.

- Zamknij ciąg w pierwszym wierszu ze znakiem podwójnego cudzysłowu i Otwórz ciąg w następnym wierszu z innym znakiem podwójnego cudzysłowu.

Zakończenie pierwszego wiersza za pomocą \n nie jest wystarczające.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2001:

```cpp
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

Spacje na początku następnego wiersza po znaku kontynuacji wiersza są uwzględniane w stałej ciągu. Żaden z przykładów pokazanych powyżej nie osadzi znaku nowego wiersza do stałej ciągu. Możesz osadzić znak nowego wiersza, jak pokazano poniżej:

```cpp
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
