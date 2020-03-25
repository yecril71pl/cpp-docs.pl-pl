---
title: Używanie operatorów w blokach __asm
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169100"
---
# <a name="using-operators-in-__asm-blocks"></a>Używanie operatorów w blokach __asm

**Specyficzne dla firmy Microsoft**

Blok `__asm` nie może używać języka C C++ lub określonych operatorów, takich jak operator **<<** . Jednak operatory udostępnione przez C i MASM, takie jak operator \*, są interpretowane jako operatory języka asemblera. Na przykład, poza blokiem `__asm`, nawiasy kwadratowe ( **[]** ) są interpretowane jako otaczające indeksy tablicy, które C automatycznie skaluje do rozmiaru elementu w tablicy. Wewnątrz bloku `__asm` są one widoczne jako operator MASM index, który daje Nieprzeskalowane bajty przesunięcie z dowolnego obiektu danych lub etykiety (nie tylko tablica). Poniższy kod ilustruje różnicę:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

Pierwsze odwołanie do `array` nie jest skalowane, ale drugi to. Należy pamiętać, że można użyć operatora **typu** , aby osiągnąć skalowanie na podstawie stałej. Na przykład następujące instrukcje są równoważne:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
