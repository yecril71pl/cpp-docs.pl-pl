---
title: Przeskakiwanie do etykiet w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 7653dc990e2f4b490bcbe333ed6f7586ac966d2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616232"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Przeskakiwanie do etykiet w asemblerze wbudowanym

**Microsoft Specific**

Jak zwykłe C lub C++ etykiety, etykiety w `__asm` bloku ma zakres w całej funkcji, w którym zdefiniowano (nie tylko w bloku). Zarówno instrukcje zestawu i `goto` instrukcji przeskoczyć do etykiety wewnątrz lub na zewnątrz `__asm` bloku.

Etykiety zdefiniowane w `__asm` bloków nie jest uwzględniana wielkość liter; obie `goto` instrukcji i instrukcje montażu mogą odwoływać się do tych etykiet bez uwzględniania wielkości liter. Etykiety C i C++ jest uwzględniana tylko wtedy, gdy jest używany przez `goto` instrukcji. Instrukcje zestawu można przeskoczyć do etykiety C lub C++ bez uwzględniania wielkości liter.

Poniższy kod pokazuje wszystkie permutacji:

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

Nie używaj nazwy funkcji biblioteki C jako etykiety w `__asm` bloków. Na przykład możesz chcieć wykorzystać do użycia `exit` jako etykietę w następujący sposób:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Ponieważ **wyjść** jest nazwą funkcji biblioteki C, ten kod może spowodować, że przechodzenie do **wyjść** zamiast funkcji do żądanej lokalizacji.

Jak MASM programy symboli dolara (`$`) stanowi bieżącą wartość licznika lokalizacji. Jest etykietę dla instrukcji obecnie składany. W `__asm` bloków, głównie jest zapewnienie przechodzi długo warunkowego:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>