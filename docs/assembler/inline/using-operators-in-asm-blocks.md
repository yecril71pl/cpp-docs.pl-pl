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
ms.openlocfilehash: a871c19942252bf6a1a4901f8854b7b759700cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166506"
---
# <a name="using-operators-in-asm-blocks"></a>Używanie operatorów w blokach __asm

**Microsoft Specific**

`__asm` Bloku nie można użyć określonego operatory C lub C++, takie jak **<<** operatora. Jednakże operatory współużytkowane przez C i MASM, takie jak \* operatora, są interpretowane jako operatorów języka asemblera. Na przykład poza `__asm` blokowanie nawiasach kwadratowych (**[**) są interpretowane jako otaczający indeksy dolne tablicy, które C jest automatycznie skalowany rozmiar elementu w tablicy. Wewnątrz `__asm` bloku, są one widoczne jako operatora indeksu MASM, która daje w wyniku przesunięcie bajtu nieskalowanego z dowolnego obiektu danych lub etykiety (nie tylko array). Poniższy kod ilustruje różnicę:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

Pierwszym odwołaniu do `array` nie jest skalowana, a w drugim. Należy zauważyć, że można użyć **typu** operatora do osiągnięcia, skalowanie w oparciu o stałą. Na przykład poniższe instrukcje są równoważne:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>