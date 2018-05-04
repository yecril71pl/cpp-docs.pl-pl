---
title: Reguły i ograniczenia dotyczące używania funkcji Naked | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb18f3e75bb7d912cbafbde01893d6283a4c61f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="rules-and-limitations-for-naked-functions"></a>Reguły i ograniczenia dotyczące używania funkcji Naked
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Do funkcji naked Zastosuj poniższe reguły i ograniczenia:  
  
-   `return` Instrukcji jest niedozwolone.  
  
-   Obsługa wyjątków strukturalnych i obsługa wyjątków języka C++ konstrukcje są niedozwolone, ponieważ muszą one unwind w ramce stosu.  
  
-   Z tego samego powodu dowolnej formy `setjmp` jest zabronione.  
  
-   Użycie `_alloca` funkcji jest zabronione.  
  
-   Aby zapewnić Brak kodu inicjowania dla zmiennych lokalnych przed sekwencji prologu, zainicjować zmienne lokalne nie są dozwolone w zakresie funkcji. W szczególności deklaracji obiektów C++ nie jest dozwolona w zakresie funkcji. Jednak można zainicjować danych w zakresie zagnieżdżonych.  
  
-   Optymalizacja wskaźnika ramki (/Oy — opcja kompilatora) nie jest zalecane, ale nie jest automatycznie wyświetlany dla funkcji naked.  
  
-   Nie można zadeklarować obiektów klasy C++ w zakresie leksykalne funkcji. Można jednak zadeklarować obiektów w zagnieżdżony blok.  
  
-   `naked` — Słowo kluczowe jest ignorowany podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Dla [__fastcall](../cpp/fastcall.md) funkcji naked, gdy istnieje odwołanie w kodzie C/C++ do jednego z argumentów rejestru, kod prologu należy przechowywać wartości rejestru do lokalizacji stosu dla tej zmiennej. Na przykład:  
  
```  
// nkdfastcl.cpp  
// compile with: /c  
// processor: x86  
__declspec(naked) int __fastcall  power(int i, int j) {  
   // calculates i^j, assumes that j >= 0  
  
   // prolog  
   __asm {  
      push ebp  
      mov ebp, esp  
      sub esp, __LOCAL_SIZE  
     // store ECX and EDX into stack locations allocated for i and j  
     mov i, ecx  
     mov j, edx  
   }  
  
   {  
      int k = 1;   // return value  
      while (j-- > 0)   
         k *= i;  
      __asm {   
         mov eax, k   
      };  
   }  
  
   // epilog  
   __asm {  
      mov esp, ebp  
      pop ebp  
      ret  
   }  
}  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji Naked](../cpp/naked-function-calls.md)