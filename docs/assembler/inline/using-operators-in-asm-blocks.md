---
title: Używanie operatorów w blokach __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2e1c7c4b8415655aff36327db9c6a9f866d82683
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051133"
---
# <a name="using-operators-in-asm-blocks"></a>Używanie operatorów w blokach __asm
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku nie można używać operatorów określonego języka C lub C++, takie jak **<<** operatora. Jednak operatory współużytkowane przez C i MASM, takich jak \* operatora, są traktowane jako operatory języka zestawu. Na przykład poza `__asm` zablokować nawiasy kwadratowe (**[**) są interpretowane jako otaczającej indeksy tablicy, w których C jest automatycznie skalowany rozmiar elementu w tablicy. Wewnątrz `__asm` bloku, są one widoczne jako operatora indeksu MASM, która daje w wyniku Przesunięcie bajtów nieskalowanego z dowolnego obiektu danych lub etykiety (nie tylko tablicą). Poniższy kod ilustruje różnicy:  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 Pierwsze odwołanie do `array` nie jest skalowana, ale drugą jest wartość. Należy pamiętać, że można użyć **typu** operator umożliwia skalowanie oparte na stałą. Na przykład następujące instrukcje są równoważne:  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)