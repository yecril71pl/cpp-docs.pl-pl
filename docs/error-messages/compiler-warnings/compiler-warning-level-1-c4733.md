---
title: Ostrzeżenie kompilatora (poziom 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 39674c32deb506725aa5f7c1f5f875e771519938
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185675"
---
# <a name="compiler-warning-level-1-c4733"></a>Ostrzeżenie kompilatora (poziom 1) C4733

Wbudowana kompilacja ASM przypisze do "FS: 0": obsługa nie jest zarejestrowana jako bezpieczna procedura obsługi

Funkcja modyfikująca wartość w usłudze FS: 0 Aby dodać nowy program obsługi wyjątków może nie działać z bezpiecznymi wyjątkami, ponieważ program obsługi może nie być zarejestrowany jako prawidłowy program obsługi wyjątków (zobacz [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Aby usunąć to ostrzeżenie, Usuń FS: 0 w definicji lub wyłączyć to ostrzeżenie i użycie [. SAFESEH](../../assembler/masm/dot-safeseh.md) , aby określić bezpieczne procedury obsługi wyjątków.

Poniższy przykład generuje C4733:

```cpp
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```
