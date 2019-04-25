---
title: Komentarze języka zestawu
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167247"
---
# <a name="assembly-language-comments"></a>Komentarze języka zestawu

**Microsoft Specific**

Zgodnie z instrukcjami w `__asm` bloku można użyć komentarze języka zestawu:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Ponieważ rozwinąć makra języka C w jednym wierszu logicznym, należy unikać używania komentarze języka zestawu w makrach. (Zobacz [Definiowanie bloków __asm jako makr C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) `__asm` Bloku może również zawierać komentarze w stylu C; Aby uzyskać więcej informacji, zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>