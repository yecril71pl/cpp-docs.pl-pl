---
title: __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- __asm
- __asm_cpp
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77e09f6af92839c6113c9c5ba375a1583bcf7149
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052680"
---
# <a name="asm"></a>__asm
**Microsoft Specific**  
  
 `__asm` — Słowo kluczowe wywołuje asemblera wbudowanego i mogą pojawiać się wszędzie tam, gdzie instrukcję języka C lub C++ jest dozwolony. Nie może pojawić się samodzielnie. Musi występować przez instrukcję zestawu, grupy instrukcji ujęta w nawiasy klamrowe, lub co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` bloku" odnosi się tutaj do dowolnego instrukcji lub grupę instrukcji, czy w nawiasach klamrowych.  
  
> [!NOTE]
>  Obsługa programu Visual C++ dla standardu C++ `asm` — słowo kluczowe jest ograniczona do fakt, że kompilator nie zostanie wygenerowany błąd on — słowo kluczowe. Jednak `asm` bloku nie wygeneruje kod łatwy do rozpoznania. Użyj `__asm` zamiast `asm`.  
  
 Składnia:  
  
 __asm *zestaw instrukcji* [;]  
  
 __asm { *zestaw instrukcji listy* } [;]  
  
## <a name="grammar"></a>Gramatyka  
 `__asm`  `assembly-instruction`  `;`OPT  
  
 `__asm {`  `assembly-instruction-list`  `};`OPT  
  
 *zestaw instrukcji listy*:  
 `assembly-instruction` `;`OPT  
  
 `assembly-instruction` `;` `assembly-instruction-list` `;`OPT  
  
 Jeśli używane bez nawiasów klamrowych, `__asm` — słowo kluczowe oznacza, że pozostała część wiersza instrukcji języka zestawu. Jeśli używana w nawiasy klamrowe, oznacza to, że każdy wiersz między nawiasy klamrowe jest instrukcji języka zestawu. Zgodność z poprzednimi wersjami `_asm` jest synonimem `__asm`.  
  
 Ponieważ `__asm` — słowo kluczowe jest separatora instrukcji, można umieścić zestaw instrukcji w tym samym wierszu.  
  
 Przed Visual C++ 2005, instrukcja  
  
```  
__asm int 3  
```  
  
 nie spowodowało natywny kod zostanie wygenerowany, gdy skompilowano z opcją **/CLR**; kompilator translacji instrukcji do instrukcji break CLR.  
  
 `__asm int 3` teraz powoduje generowanie kodu natywnego dla funkcji. Jeśli chcesz, aby spowodować punkt przerwania w kodzie i że funkcja, skompilowane do MSIL, należy użyć funkcji [__debugbreak](../../intrinsics/debugbreak.md).  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu jest prostą `__asm` bloku ujęta w nawiasy klamrowe:  
  
```  
__asm {  
   mov al, 2  
   mov dx, 0xD007  
   out dx, al  
}  
```  
  
 Alternatywnie można umieścić `__asm` na początku każdego zestawu instrukcji:  
  
```  
__asm mov al, 2  
__asm mov dx, 0xD007  
__asm out dx, al  
```  
  
 Ponieważ `__asm` — słowo kluczowe jest separatora instrukcji, można również wprowadzić zestaw instrukcji w tym samym wierszu:  
  
```  
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al  
```  
  
 Wszystkie trzy przykłady Generowanie tego samego kodu, ale pierwszego stylu (otaczającej `__asm` blok w nawiasach klamrowych) ma pewne zalety. Nawiasy klamrowe wyraźnie oddzielić kodu zestawu z kodu języka C lub C++ i uniknąć niepotrzebnego powtarzania `__asm` — słowo kluczowe. Nawiasy klamrowe również może uniemożliwić niejednoznaczności. Jeśli chcesz umieścić instrukcję języka C lub C++ w tym samym wierszu co `__asm` bloku, blok należy ująć w nawiasach klamrowych. Bez nawiasów klamrowych kompilator nie wiadomo, gdzie rozpocząć instrukcjach języka C lub C++ i zatrzymuje kodu zestawu. Na koniec ponieważ tekst w nawiasach klamrowych ma ten sam format, jako zwykły tekst MASM, można łatwo wyciąć i wkleić tekst z istniejących plików źródłowych MASM.  
  
 W odróżnieniu od nawiasy klamrowe w C i C++, nawiasy otaczającej `__asm` bloku nie wpływają na zakres zmiennej. Można zagnieżdżać `__asm` bloków; zagnieżdżenia ma nie ma wpływu na zakres zmiennej.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../../cpp/keywords-cpp.md)   
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)