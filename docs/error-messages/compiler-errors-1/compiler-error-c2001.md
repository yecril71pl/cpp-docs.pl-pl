---
title: Błąd kompilatora C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756841"
---
# <a name="compiler-error-c2001"></a>Błąd kompilatora C2001

stała nowego wiersza

Stała ciągu nie może być kontynuowana w drugim wierszu, chyba że wykonasz następujące czynności:

- Zakończ pierwszy wiersz za pomocą ukośnika odwrotnego.

- Zamknij ciąg w pierwszym wierszu ze znakiem podwójnego cudzysłowu i Otwórz ciąg w następnym wierszu z innym znakiem podwójnego cudzysłowu.

Zakończenie pierwszego wiersza za pomocą \n nie jest wystarczające.

## <a name="example"></a>Przykład

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

## <a name="example"></a>Przykład

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
