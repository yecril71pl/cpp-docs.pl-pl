---
title: Wywoływanie funkcji C w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 94bbfda3a5fd15885f3d8276d506541418a9489f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169594"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Blok `__asm` może wywoływać funkcje C, w tym procedury biblioteki języka C. Poniższy przykład wywołuje procedurę biblioteki `printf`:

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Ponieważ argumenty funkcji są przekazywane na stosie, po prostu wypchnij potrzebne argumenty — wskaźniki ciągu, w poprzednim przykładzie — przed wywołaniem funkcji. Argumenty są wypychane w odwrotnej kolejności, dlatego są wychodzące ze stosu w odpowiedniej kolejności. Aby emulować instrukcję języka C

```cpp
printf( format, hello, world );
```

przykład wypchnięcie wskaźników do `world`, `hello`i `format`w tej kolejności, a następnie wywołuje `printf`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
