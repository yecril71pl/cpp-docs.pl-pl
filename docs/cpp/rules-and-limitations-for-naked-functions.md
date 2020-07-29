---
title: Reguły i ograniczenia dotyczące używania funkcji Naked
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: 3dd089e13323e1811cf9d7c7717612313f2cef7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225855"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Reguły i ograniczenia dotyczące używania funkcji Naked

**Specyficzne dla firmy Microsoft**

Następujące reguły i ograniczenia mają zastosowanie do funkcji niezwiązanych z wypełnieniem:

- **`return`** Instrukcja jest niedozwolona.

- Konstrukcje strukturalne obsługujące wyjątki i obsługa wyjątków C++ są niedozwolone, ponieważ muszą być rozwinięcia między ramką stosu.

- Z tego samego powodu jakakolwiek forma `setjmp` jest niedozwolona.

- Użycie `_alloca` funkcji jest zabronione.

- Aby upewnić się, że żaden kod inicjujący dla zmiennych lokalnych nie występuje przed sekwencją prologu, zainicjowane zmienne lokalne nie są dozwolone w zakresie funkcji. W szczególności deklaracja obiektów C++ nie jest dozwolona w zakresie funkcji. Można jednak inicjować dane w zakresie zagnieżdżonym.

- Optymalizacja wskaźnika ramki (opcja kompilatora/Oy) nie jest zalecana, ale jest automatycznie pomijana dla funkcji wydzielania.

- Nie można zadeklarować obiektów klas C++ w zakresie leksykalnym funkcji. Można jednak zadeklarować obiekty w bloku zagnieżdżonym.

- **`naked`** Słowo kluczowe jest ignorowane podczas kompilowania z [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

- W przypadku [__fastcall](../cpp/fastcall.md) , gdy w kodzie C/C++ istnieje odwołanie do jednego z argumentów rejestru, kod prologu powinien przechowywać wartości rejestru w lokalizacji stosu dla tej zmiennej. Na przykład:

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wywołania funkcji bez nadruku](../cpp/naked-function-calls.md)
