---
title: Błąd kompilatora C2001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088245"
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