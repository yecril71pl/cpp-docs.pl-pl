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
ms.openlocfilehash: 199156a08af13f4a70793609b37c70b0c95bf9ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169334"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Przeskakiwanie do etykiet w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Podobnie jak zwykła C lub C++ etykieta, etykieta w bloku `__asm` ma zakres w całej funkcji, w której jest zdefiniowany (nie tylko w bloku). Instrukcje dotyczące zestawu i instrukcje `goto` mogą przeskoczyć do etykiet wewnątrz lub na zewnątrz bloku `__asm`.

Etykiety zdefiniowane w blokach `__asm` nie uwzględniają wielkości liter. instrukcje `goto` instrukcji i zestawu mogą odwoływać się do tych etykiet bez względu na wielkość liter. W języku C++ C i etykietach jest rozróżniana wielkość liter, gdy są używane przez instrukcje `goto`. Instrukcje zestawu mogą przeskoczyć do etykiety C C++ lub bez względu na wielkość liter.

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

Nie używaj nazw funkcji biblioteki języka C jako etykiet w blokach `__asm`. Na przykład możesz być skłonny do używania `exit` jako etykiety w następujący sposób:

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

Podobnie jak w przypadku programów MASM symbol dolara (`$`) służy jako bieżąca wartość licznika lokalizacji. Jest to etykieta dla aktualnie składanej instrukcji. W blokach `__asm`, jego głównym zastosowaniem jest wykonywanie długich skoków warunkowych:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
