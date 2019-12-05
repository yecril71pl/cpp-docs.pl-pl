---
title: Reguły i ograniczenia dotyczące używania funkcji Naked
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: ec5c7d635dbbb63af7177395c5ad08356e1a26f0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857310"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Reguły i ograniczenia dotyczące używania funkcji Naked

**Microsoft Specific**

Następujące reguły i ograniczenia mają zastosowanie do funkcji niezwiązanych z wypełnieniem:

- Instrukcja **Return** jest niedozwolona.

- Konstrukcje strukturalne obsługujące wyjątki i C++ obsługa wyjątków są niedozwolone, ponieważ muszą być rozwinięcia między ramką stosu.

- Z tego samego powodu dowolna forma `setjmp` jest zabroniona.

- Użycie funkcji `_alloca` jest zabronione.

- Aby upewnić się, że żaden kod inicjujący dla zmiennych lokalnych nie występuje przed sekwencją prologu, zainicjowane zmienne lokalne nie są dozwolone w zakresie funkcji. W szczególności deklaracja C++ obiektów nie jest dozwolona w zakresie funkcji. Można jednak inicjować dane w zakresie zagnieżdżonym.

- Optymalizacja wskaźnika ramki (opcja kompilatora/Oy) nie jest zalecana, ale jest automatycznie pomijana dla funkcji wydzielania.

- Nie można zadeklarować C++ obiektów klasy w zakresie leksykalnym funkcji. Można jednak zadeklarować obiekty w bloku zagnieżdżonym.

- Słowo kluczowe " **owies** " jest ignorowane podczas kompilowania z [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

- W przypadku [__fastcall](../cpp/fastcall.md) , gdy istnieje odwołanie w C/C++ Code do jednego z argumentów rejestru, kod prologu powinien przechowywać wartości rejestru w lokalizacji stosu dla tej zmiennej. Na przykład:

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

[Wywołania funkcji Naked](../cpp/naked-function-calls.md)