---
title: Pisanie funkcji w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6c6c5b064dfc7d156d4de424e1ab69d74140f90
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="writing-functions-with-inline-assembly"></a>Pisanie funkcji w zestawie wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Jeśli piszesz funkcji z kodu zestawu wbudowanego jest łatwo przekazywać argumenty do funkcji i zwracanie wartości z jej. Poniższe przykłady porównanie funkcji najpierw napisane dla oddzielnych asemblera i ulegną asemblera wbudowanego. Wywołana funkcja `power2`, otrzymuje dwa parametry pomnożenie pierwszy parametr przez 2 do potęgi drugiego parametru. Przeznaczone dla oddzielnych asemblera, funkcja może wyglądać następująco:  
  
```  
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
  
 Ponieważ jest ona zapisywana na oddzielnych asemblera, funkcja wymaga kroki oddzielne źródło pliku i zestaw oraz łącza. Argumenty funkcji C i C++ zwykle są przekazywane na stosie, dlatego ta wersja `power2` funkcja uzyskuje dostęp do argumentów według ich pozycji na stosie. (Należy pamiętać, że **modelu** dyrektywy dostępne w MASM i innych asemblerów umożliwia również dostęp do argumentów stosu i zmienne lokalne, stos według nazwy.)  
  
## <a name="example"></a>Przykład  
 Zapisuje ten program `power2` funkcji z kodu zestawu wbudowanego:  
  
```  
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
  
 Wersja wbudowanego `power2` funkcji odwołuje się do jego argumentów według nazwy i pojawia się w tym samym pliku źródłowego, jako całego programu. Ta wersja również wymaga mniej instrukcje zestawu.  
  
 Ponieważ wersja wbudowanego `power2` nie jest wykonywana C `return` instrukcji, powoduje nieszkodliwe ostrzeżenie, jeśli kompilacja na poziomie ostrzeżenia 2 lub nowszej. Funkcja zwraca wartość, ale kompilator nie wiadomo, że w przypadku braku `return` instrukcji. Można użyć [ostrzeżenie #pragma](../../preprocessor/warning.md) Aby wyłączyć generowanie to ostrzeżenie.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)