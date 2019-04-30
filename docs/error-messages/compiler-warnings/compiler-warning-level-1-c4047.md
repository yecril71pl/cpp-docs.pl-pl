---
title: Kompilator ostrzeżenie (poziom 1) C4047
ms.date: 11/04/2016
f1_keywords:
- C4047
helpviewer_keywords:
- C4047
ms.assetid: b75ad6fb-5c93-4434-a85f-c4083051a5de
ms.openlocfilehash: 87c9e39e5dac40341adc63af45cc0e460806c736
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388829"
---
# <a name="compiler-warning-level-1-c4047"></a>Kompilator ostrzeżenie (poziom 1) C4047

'operator': "identifier1" różni się w poziomach pośredników od "identifier2"

Zmienna (jeden poziom pośredni), wskazać wskaźnik do innego wskaźnika, który wskazuje zmienna (dwa poziomy pośredni) i tak dalej.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4047:

```
// C4047.c
// compile with: /W1

int main() {
   char **p = 0;   // two levels of indirection
   char *q = 0;   // one level of indirection

   char *p2 = 0;   // one level of indirection
   char *q2 = 0;   // one level of indirection

   p = q;   // C4047
   p2 = q2;
}
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4047:

```
// C4047b.c
// compile with: /W1
#include <stdio.h>

int main() {
   int i;
   FILE *myFile = NULL;
   errno_t  err = 0;
   char file_name[256];
   char *cs = 0;

   err = fopen_s(&myFile, "C4047.txt", "r");
   if ((err != 0) || (myFile)) {
      printf_s("fopen_s failed!\n");
      exit(-1);
    }
   i = fgets(file_name, 256, myFile);   // C4047
   cs = fgets(file_name, 256, myFile);   // OK
}
```