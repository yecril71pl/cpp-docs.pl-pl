---
title: Kompilator ostrzeżenie (poziom 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 0d0b0b912ef15294f9a4362a79dffd6d7eeabed8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221118"
---
# <a name="compiler-warning-level-1-c4733"></a>Kompilator ostrzeżenie (poziom 1) C4733

Przypisanie w wbudowanym do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa

Funkcję, zmieniając wartość w FS:0, aby dodać nowy program obsługi wyjątków może nie działać z bezpiecznych wyjątków, ponieważ program obsługi nie może zostać zarejestrowana jako prawidłowej procedury obsługi wyjątków (zobacz [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Aby rozwiązać tego ostrzeżenia, albo usuń definicję FS:0 lub wyłączyć to ostrzeżenie i użyj [. SAFESEH](../../assembler/masm/dot-safeseh.md) do określenia obsługi bezpiecznych wyjątków.

Poniższy przykład spowoduje wygenerowanie C4733:

```
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