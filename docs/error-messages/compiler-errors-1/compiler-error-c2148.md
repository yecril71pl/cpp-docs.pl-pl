---
title: Błąd kompilatora C2148
ms.date: 11/04/2016
f1_keywords:
- C2148
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
ms.openlocfilehash: 893f1f029b2ea1aaf7ff53a5ee5cee7fcbe36e7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440355"
---
# <a name="compiler-error-c2148"></a>Błąd kompilatora C2148

Całkowity rozmiar tablicy nie może przekraczać 0x7fffffff bajtów

Tablica przekracza limit. Zmniejsz rozmiar tablicy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2148:

```
// C2148.cpp
#include <stdio.h>
#include <stdlib.h>

int main( ) {
   char MyArray[0x7ffffffff];   // C2148
   char * MyArray2 = (char *)malloc(0x7fffffff);

   if (MyArray2)
      printf_s("It worked!");
   else
      printf_s("It didn't work.");
}
```