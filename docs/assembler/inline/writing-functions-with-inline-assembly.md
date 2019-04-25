---
title: Pisanie funkcji w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 7848a8f071f50f8d809a999a96a9c0f8193c480e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166857"
---
# <a name="writing-functions-with-inline-assembly"></a>Pisanie funkcji w zestawie wbudowanym

**Microsoft Specific**

Jeśli piszesz funkcji z kodem asemblera wbudowanego, jest łatwo przekazywać argumenty do funkcji i zwracanie wartości z niego. W następującym przykładzie porównano funkcji najpierw jest przeznaczony dla stosowania oddzielnego asemblera i ulegną asemblera wbudowanego. Wywołana funkcja `power2`, otrzymuje dwa parametry, mnożenie pierwszy parametr przez 2 do potęgi równej drugi parametr. Przeznaczony dla stosowania oddzielnego asemblera, funkcja może wyglądać następująco:

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

Ponieważ jest on przeznaczony dla stosowania oddzielnego asemblera, funkcja wymaga kroki oddzielne źródło pliku i asemblacji i łączenia. C i C++ argumenty funkcji są zazwyczaj przekazywane na stosie, dlatego ta wersja `power2` funkcja uzyskuje dostęp do argumentów według ich położenia na stosie. (Należy pamiętać, że **modelu** dyrektywy, dostępne w MASM i innych asemblerów umożliwia również dostęp do argumentów stosu i zmiennych lokalnych stosu według nazwy.)

## <a name="example"></a>Przykład

Ten program zapisuje `power2` funkcji z wbudowany kod asemblera:

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

Wbudowane wersję `power2` funkcja odnosi się do jego argumentów według nazwy i pojawia się w tym samym pliku źródłowym jako pozostałej części programu. Ta wersja również wymaga mniejszej liczby instrukcje zestawu.

Ponieważ wbudowane wersję `power2` nie jest wykonywany C `return` instrukcji powoduje nieszkodliwe ostrzeżenie w przypadku kompilacji na poziom ostrzeżeń 2 lub nowszej. Funkcja zwraca wartość, ale kompilator nie wiadomo, że w przypadku braku `return` instrukcji. Możesz użyć [ostrzeżenie #pragma](../../preprocessor/warning.md) Aby wyłączyć generowanie to ostrzeżenie.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>