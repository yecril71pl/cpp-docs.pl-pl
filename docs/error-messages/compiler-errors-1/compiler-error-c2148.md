---
title: Błąd kompilatora C2148 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2148
dev_langs:
- C++
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8e76228ff585f47a2cbe210ac3eb96d5d281a93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114023"
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