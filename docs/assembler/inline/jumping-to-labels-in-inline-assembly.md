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
ms.openlocfilehash: 0c411289745466bd6478cc82ab30e6a05be9cc25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192005"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Przeskakiwanie do etykiet w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Podobnie jak zwykła etykieta C lub C++, etykieta w **`__asm`** bloku ma zakres w całej funkcji, w której jest zdefiniowany (nie tylko w bloku). Instrukcje zestawu i instrukcje **`goto`** mogą przeskoczyć do etykiet wewnątrz lub na zewnątrz **`__asm`** bloku.

Etykiety zdefiniowane w **`__asm`** blokach nie uwzględniają wielkości liter. obie instrukcje **`goto`** i instrukcje dotyczące zestawu mogą odwoływać się do tych etykiet bez względu na wielkość liter. Etykiety C i C++ uwzględniają wielkość liter tylko wtedy, gdy są używane przez **`goto`** instrukcje. Instrukcje zestawu mogą przeskoczyć do etykiety C lub C++ bez względu na wielkość liter.

Poniższy kod przedstawia wszystkie permutacje:

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

Nie używaj nazw funkcji biblioteki języka C jako etykiet w **`__asm`** blokach. Na przykład może być skłonny do użycia `exit` jako etykieta w następujący sposób:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Ponieważ **Exit** jest nazwą funkcji biblioteki języka C, ten kod może spowodować przeskoczenie do funkcji **Exit** zamiast do żądanej lokalizacji.

Podobnie jak w przypadku programów MASM symbol dolara ( `$` ) służy jako bieżący licznik lokalizacji. Jest to etykieta dla aktualnie składanej instrukcji. W **`__asm`** blokach jego głównym zastosowaniem jest wykonywanie długich skoków warunkowych:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
