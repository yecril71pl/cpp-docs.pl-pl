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
ms.openlocfilehash: 4d12321cd90f596c94c2337e100663436d512107
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435350"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C w asemblerze wbudowanym

**Microsoft Specific**

`__asm` Bloku można wywołać funkcji języka C, w tym C biblioteki procedur. Poniższy przykład wywołuje `printf` procedury biblioteki:

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

Ponieważ argumenty funkcji są przekazywane na stosie, po prostu wypychania wymagane argumenty — ciąg wskaźników w poprzednim przykładzie — przed wywołaniem funkcji. Argumenty są przekazywane w odwrotnej kolejności, więc pochodzą ze stosu w odpowiedni sposób. Aby emulować instrukcji C

```cpp
printf( format, hello, world );
```

przykład wypycha wskaźniki do `world`, `hello`, i `format`, w tej kolejności, a następnie wywołania `printf`.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>