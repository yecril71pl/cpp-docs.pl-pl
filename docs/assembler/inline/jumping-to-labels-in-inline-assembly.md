---
title: Przeskakiwanie do etykiet w asemblerze wbudowanym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1170a12aefeb53083d5627b1b84639403ea17182
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Przeskakiwanie do etykiet w asemblerze wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Zwykłe C lub C++ etykiety, etykieta w, takich jak `__asm` bloku ma zakres w całej funkcji, w którym jest zdefiniowany (nie tylko w bloku). Zarówno instrukcje zestawu i `goto` instrukcji można przejść do etykiety wewnątrz lub na zewnątrz `__asm` bloku.  
  
 Etykiet zdefiniowanych w `__asm` bloków nie jest uwzględniana; oba `goto` instrukcje i instrukcje zestawu mogą odwoływać się do tych etykiet bez uwzględniania wielkości liter. C i C++ etykiety jest uwzględniana wielkość liter tylko wtedy, gdy jest używany przez `goto` instrukcje. Zestaw instrukcji można przejść do języka C lub C++ Etykieta bez uwzględniania wielkości liter.  
  
 Poniższy kod przedstawia wszystkie permutacji:  
  
```  
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
  
 Nie używaj nazwy funkcji biblioteki C jako etykiety w `__asm` bloków. Na przykład może się wydawać się użyć `exit` jako etykietę w następujący sposób:  
  
```  
; BAD TECHNIQUE: using library function name as label  
jne exit  
   .  
   .  
   .  
exit:  
   ; More __asm code follows  
```  
  
 Ponieważ **zakończyć** jest nazwą funkcji biblioteki C, ten kod może spowodować, że przechodzenie do **zakończyć** funkcji zamiast do odpowiedniej lokalizacji.  
  
 Jak programy MASM, symbol dolara (`$`) służy jako licznik bieżącej lokalizacji. Jest etykieta instrukcji aktualnie połączone. W `__asm` bloków, głównie jest zapewnienie przechodzi długo warunkowego:  
  
```  
jne $+5 ; next instruction is 5 bytes long  
jmp farlabel  
; $+5  
   .  
   .  
   .  
farlabel:  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)