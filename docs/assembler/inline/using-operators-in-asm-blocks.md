---
title: Używanie operatorów w blokach __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8731169013cba50e01c36aa721859e136938f015
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676913"
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