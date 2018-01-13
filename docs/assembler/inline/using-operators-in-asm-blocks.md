---
title: "Używanie operatorów w blokach __asm | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca8ac739793c81ef18f8657cbf53c9cb018b3e38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-operators-in-asm-blocks"></a>Używanie operatorów w blokach __asm
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku nie można używać operatorów określonego języka C lub C++, takie jak  **<<**  operatora. Jednak operatory współużytkowane przez C i MASM, takich jak \* operatora, są traktowane jako operatory języka zestawu. Na przykład poza `__asm` zablokować nawiasy kwadratowe (**[**) są interpretowane jako otaczającej indeksy tablicy, w których C jest automatycznie skalowany rozmiar elementu w tablicy. Wewnątrz `__asm` bloku, są one widoczne jako operatora indeksu MASM, która daje w wyniku Przesunięcie bajtów nieskalowanego z dowolnego obiektu danych lub etykiety (nie tylko tablicą). Poniższy kod ilustruje różnicy:  
  
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