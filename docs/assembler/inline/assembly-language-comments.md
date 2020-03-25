---
title: Komentarze języka zestawu
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169607"
---
# <a name="assembly-language-comments"></a>Komentarze języka zestawu

**Specyficzne dla firmy Microsoft**

Instrukcje w bloku `__asm` mogą korzystać z komentarzy do języka zestawu:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Ponieważ makra języka C są rozwijane do pojedynczej linii logicznej, Unikaj korzystania z komentarzy w języku asemblera w makrach. (Zobacz [Definiowanie bloków __asm jako makr C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)). Blok `__asm` może również zawierać komentarze w stylu C; Aby uzyskać więcej informacji, zobacz [Używanie języka C++ C lub w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
