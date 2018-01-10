---
title: Inline Assembler (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22d27d5ad63bd92558569bfa211e3c58d5677a27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inline-assembler-c"></a>Asembler wbudowany (C)
**Dotyczące firmy Microsoft**  
  
 Asembler wbudowany umożliwia osadzanie instrukcje języka zestawu bezpośrednio w programach źródła C bez dodatkowego zestawu i kroki łącza. Asembler wbudowany jest wbudowana w kompilatorze — nie ma potrzeby oddzielnego asemblera takich jak Microsoft asemblera makr (MASM).  
  
 Asembler wbudowany nie wymagają osobny zestaw i kroki łącze, jest wygodniejsze niż oddzielne asemblera. Kod zestawu wbudowanego można użyć dowolnego C zmienną lub funkcję nazwę, która znajduje się w zakresie, dlatego łatwo zintegrować ją z kodem C z programem. I ponieważ kodu zestawu można łączyć instrukcji C, można go do zadania, które są skomplikowane lub niemożliwe w języku C samodzielnie.  
  
 `__asm` — Słowo kluczowe wywołuje asemblera wbudowanego i może występować we wszystkich instrukcji C jest dozwolony. Nie może pojawić się samodzielnie. Musi występować przez instrukcję zestawu, grupy instrukcji ujęta w nawiasy klamrowe, lub co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` bloku" odnosi się tutaj do dowolnego instrukcji lub grupę instrukcji, czy w nawiasach klamrowych.  
  
 Poniższy kod jest prosty `__asm` bloku ujęta w nawiasy klamrowe. (Kod jest sekwencją prologu funkcji niestandardowej).  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
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
 [Atrybuty funkcji](../c-language/function-attributes.md)