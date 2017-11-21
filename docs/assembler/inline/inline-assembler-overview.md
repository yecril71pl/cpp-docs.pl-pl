---
title: "Przegląd asemblera wbudowanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7733398f5a444fa5e7461ea52295624d6d16f9a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inline-assembler-overview"></a>Omówienie wbudowanego asemblera
**Dotyczące firmy Microsoft**  
  
 Asembler wbudowany umożliwia osadzanie instrukcje języka zestawu w Twoje programy źródłowe C i C++ bez dodatkowych czynności zestawu i łącza. Asembler wbudowany jest wbudowana w kompilatorze — nie ma potrzeby oddzielnego asemblera takich jak Microsoft asemblera makr (MASM).  
  
 Asembler wbudowany nie wymagają osobny zestaw i kroki łącze, jest wygodniejsze niż oddzielne asemblera. Kod zestawu wbudowanego można użyć dowolnego języka C lub C++ zmienną lub funkcję nazwę, która znajduje się w zakresie, dlatego łatwo zintegrować ją z kodem C i C++ z programem. I ponieważ kodu zestawu można łączyć instrukcji C i C++, można go do zadania, które są skomplikowane lub niemożliwe w języka C lub C++ samodzielnie.  
  
 [__Asm](../../assembler/inline/asm.md) — słowo kluczowe wywołuje asemblera wbudowanego i mogą pojawiać się wszędzie tam, gdzie instrukcję języka C lub C++ jest dozwolony. Nie może pojawić się samodzielnie. Musi występować przez instrukcję zestawu, grupy instrukcji ujęta w nawiasy klamrowe, lub co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` bloku" odnosi się tutaj do dowolnego instrukcji lub grupę instrukcji, czy w nawiasach klamrowych.  
  
 Następujący kod jest prosty `__asm` bloku ujęta w nawiasy klamrowe. (Kod jest sekwencją prologu funkcji niestandardowej).  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
}  
```  
  
 Alternatywnie można umieścić `__asm` na początku każdego zestawu instrukcji:  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 Ponieważ `__asm` — słowo kluczowe jest separatora instrukcji, można również wprowadzić zestaw instrukcji w tym samym wierszu:  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Asembler wbudowany](../../assembler/inline/inline-assembler.md)