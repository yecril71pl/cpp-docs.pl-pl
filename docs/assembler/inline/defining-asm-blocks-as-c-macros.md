---
title: "Definiowanie bloków __asm jako makr C | Dokumentacja firmy Microsoft"
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
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af95f7b2c74d797203a0e6b3ddd6a92ddcb51e5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="defining-asm-blocks-as-c-macros"></a>Definiowanie bloków __asm jako makr C
**Dotyczące firmy Microsoft**  
  
 Makra C oferują wygodny sposób, aby wstawić kod zestawu do kodu źródłowego, ale zażądać szczególną uwagę, ponieważ rozszerza makra w jednym wierszu logicznym. Aby utworzyć bezproblemowe makra, należy wykonać następujące czynności:  
  
-   Umieść `__asm` blok w nawiasach klamrowych.  
  
-   Umieść `__asm` — słowo kluczowe przed każdą instrukcję zestawu.  
  
-   Użyj stary styl komentarze języka C ( `/* comment */`) zamiast zestawu w stylu ( `; comment`) lub jeden wiersz komentarze języka C ( `// comment`).  
  
 Aby zilustrować, w poniższym przykładzie zdefiniowano proste makra:  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 Na pierwszy rzut, ostatnich trzech `__asm` zbędny prawdopodobnie słów kluczowych. Są one potrzebne, jednakże, ponieważ rozszerza makra w jednym wierszu:  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 Trzecia i czwarta `__asm` wymagane są słowa kluczowe jako separatorów instrukcji. Rozpoznany separatorów jedyną instrukcją w `__asm` bloki są znaku nowego wiersza i `__asm` — słowo kluczowe. Ponieważ blok zdefiniowany jako makra jest jednym wierszu logicznym, muszą być rozdzielone każdej instrukcji z `__asm`.  
  
 Nawiasy klamrowe są niezbędne, jak również. W przypadku pominięcia ich kompilator można pomylić przez wyrażenia języka C lub C++ w tym samym wierszu w prawo wywołanie makra. Bez zamykający nawias klamrowy, kompilator nie wiadomo, gdzie zatrzymuje kodu zestawu który zobaczy instrukcji języka C lub C++ `__asm` bloku jako zestaw instrukcji.  
  
 Komentarze zestawu stylu, rozpoczynające się średnikiem (**;**) nadal końca wiersza. Wystąpił problem w makrach ponieważ kompilator ignoruje całą zawartość po komentarz, aż do końca wiersza logiczne. To samo dotyczy jednowierszowego komentarza C lub C++ ( `// comment`). Aby zapobiec błędom, używając komentarzy C w starym stylu ( `/* comment */`) w `__asm` bloki zdefiniowany jako makra.  
  
 `__asm` Bloku jako makr C może zająć argumentów. W odróżnieniu od zwykłego C makra, jednak `__asm` makro nie może zwracać wartości. Dlatego takie makra nie można używać w wyrażeniach języka C lub C++.  
  
 Nie można więc przyrostu wywołanie makra tego typu. Na przykład wywoływania makra języka zestawu w funkcji zadeklarowana z `__fastcall` Konwencji może spowodować nieoczekiwane wyniki. (Zobacz [przy użyciu rejestrów i zachowanie ich w zestawie wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)