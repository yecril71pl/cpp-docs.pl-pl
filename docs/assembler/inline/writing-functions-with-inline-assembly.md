---
title: Pisanie funkcji w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 5416a29477651c496d83e6ee215a2cb88ba26e3b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169061"
---
# <a name="writing-functions-with-inline-assembly"></a>Pisanie funkcji w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Jeśli piszesz funkcję z wbudowanym kodem zestawu, można łatwo przekazywać argumenty do funkcji i zwracać wartość z niej. Poniższe przykłady porównują funkcję, która najpierw została zapisywana dla oddzielnego asemblera, a następnie ponownie napisano dla asemblera wbudowanego. Funkcja o nazwie `power2`odbiera dwa parametry, mnożąc pierwszy parametr o wartość 2 do potęgi drugiego parametru. W przypadku osobnego asemblera funkcja może wyglądać następująco:

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

Ponieważ jest zapisywana dla oddzielnego asemblera, funkcja wymaga oddzielnego pliku źródłowego oraz zestawu i kroków łącza. Argumenty funkcji C++ C i są zwykle przekazane na stosie, więc ta wersja funkcji `power2` uzyskuje dostęp do jej argumentów przez ich pozycje na stosie. (Należy zauważyć, że dyrektywa **modelu** , dostępna w MASM i innych asemblerach, umożliwia również dostęp do argumentów stosu i lokalnych zmiennych stosu według nazwy).

## <a name="example"></a>Przykład

Ten program zapisuje funkcję `power2` przy użyciu wbudowanego kodu zestawu:

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

Wersja wbudowana funkcji `power2` odnosi się do jej argumentów według nazwy i pojawia się w tym samym pliku źródłowym co reszta programu. Ta wersja wymaga również mniej instrukcji dotyczących zestawu.

Ponieważ wbudowana wersja `power2` nie wykonuje instrukcji C `return`, powoduje to nieszkodliwe Ostrzeżenie w przypadku kompilowania na poziomie ostrzeżeń 2 lub wyższym. Funkcja zwraca wartość, ale kompilator nie może stwierdzić, czy w nieobecności instrukcji `return`. Aby wyłączyć generowanie tego ostrzeżenia, można użyć [ostrzeżenia #pragma](../../preprocessor/warning.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
