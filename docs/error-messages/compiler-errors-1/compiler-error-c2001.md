---
title: Błąd kompilatora C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 03b54fe2373063c8c0f9905da93822928392998d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596368"
---
# <a name="compiler-error-c2001"></a>Błąd kompilatora C2001

Nowy wiersz w stałej

Stała typu string nie mogą być kontynuowane w drugim wierszu, chyba, że wykonano następujące czynności:

- Koniec pierwszego wiersza znakiem kreski ułamkowej odwróconej.

- Zamknij ciąg znaków w pierwszym wierszu za pomocą podwójnego cudzysłowu i otwórz ciągu w następnym wierszu za pomocą innego podwójny cudzysłów.

Kończenie pierwszy wiersz z \n jest niewystarczająca.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2001:

```
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

Miejsca do magazynowania na początku następnego wiersza po znaku kontynuacji wiersza są objęte stała typu string. Żaden z przykładów pokazanych powyżej osadzić znak nowego wiersza w stała typu string. Możesz osadzić znak nowego wiersza, jak pokazano poniżej:

```
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