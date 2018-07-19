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
ms.openlocfilehash: c1a6f88717b8fb371c343d17a9b38608876cd900
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947786"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Reguły i ograniczenia dotyczące używania funkcji Naked
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Poniższe reguły i ograniczenia dotyczą funkcji "naked":  
  
-   **Zwracają** instrukcja nie jest dozwolone.  
  
-   Konstrukcje obsługi wyjątków strukturalnych i obsługa wyjątków języka C++ nie są dozwolone, ponieważ one muszą operacji unwind WE ramki stosu.  
  
-   Z tego samego powodu jakiejkolwiek formy `setjmp` jest zabronione.  
  
-   Korzystanie z `_alloca` funkcji jest zabronione.  
  
-   Aby upewnić się, że żaden kod inicjowania dla zmiennych lokalnych jest umieszczany przed sekwencji prologu, zainicjować zmienne lokalne są niedozwolone w zakresie funkcji. W szczególności deklaracja obiektów C++ nie jest dozwolona w zakresie funkcji. W zakresie zagnieżdżonych jednak może być zainicjowany danych.  
  
-   Optymalizacja wskaźnik ramki (/Oy — opcja kompilatora) nie jest zalecane, ale nie jest automatycznie wyświetlany dla funkcji "naked".  
  
-   Nie można zadeklarować obiektów klasy języka C++ w zakresie leksykalnym funkcji. Możesz jednak zadeklarować obiekty zagnieżdżony blok.  
  
-   **"Naked"** — słowo kluczowe jest ignorowany podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Aby uzyskać [__fastcall](../cpp/fastcall.md) funkcji "naked" zawsze wtedy, gdy istnieje odwołanie w kodzie języka C/C++ do jednego z argumentów rejestru, w kodzie prologu powinny być przechowywane wartości rejestru do lokalizacji stosu dla tej zmiennej. Na przykład:  
  
```cpp 
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
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji Naked](../cpp/naked-function-calls.md)