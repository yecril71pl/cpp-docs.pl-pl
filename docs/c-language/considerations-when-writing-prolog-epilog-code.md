---
title: Zagadnienia dotyczące pisania kodu prologu/epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: 52403fc45bbb68d693ef154bf39c5dd366dd10c5
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146485"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu

**Microsoft Specific**

Przed napisaniem własnej sekwencji kodu prologu i epilogu należy zrozumieć ułożenie ramki stosu. Warto też wiedzieć, jak używać **__LOCAL_SIZE** wstępnie zdefiniowanej stałej.

##  <a name="_clang_c_stack_frame_layout"></a> Układ ramki stosu C

W tym przykładzie pokazano standardowy kod prologu, który może pojawić się w 32-bitowej funkcji:

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

Zmienna `localbytes` reprezentuje liczbę bajtów potrzebnych na stosie dla zmiennych lokalnych a zmienna `registers` jest symbolem zastępczym reprezentującym listę rejestrów, które mają być zapisane na stosie. Po umieszczeniu rejestrów na stosie, można tam umieścić wszelkie inne dane. Poniżej przedstawiono odpowiadający kod epilogu:

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

Stos zawsze powiększa się w dół (od najwyższego do najniższego adresu pamięci). Podstawowy wskaźnik (`ebp`) wskazuje na umieszczoną wartość `ebp`. Obszar zmiennych lokalnych rozpoczyna się od `ebp-2`. Aby uzyskać dostęp do zmiennych lokalnych, należy obliczyć przesunięcie z `ebp` przez odjęcie odpowiedniej wartości od `ebp`.

##  <a name="_clang_the___local_size_constant"></a> __LOCAL_SIZE — stała

Kompilator zapewnia stałą **__LOCAL_SIZE**, do użycia w bloku asemblera wbudowanego w kodzie prologu funkcji. Stała jest używana do alokowania miejsca dla zmiennych lokalnych na ramce stosu w niestandardowym kodzie prologu.

Kompilator określa wartość **__LOCAL_SIZE**. Wartość to całkowita liczba bajtów wszystkich zmiennych lokalnych zdefiniowanych przez użytkownika i zmiennych tymczasowych wygenerowanych przez kompilator. **__LOCAL_SIZE** mogą być używane tylko jako bezpośredni argument; nie można używać w wyrażeniach. Nie wolno zmieniać lub ponownie definiować wartości tej stałej. Na przykład:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

Poniższy przykład funkcji "naked", zawierający niestandardową sekwencję prologu i epilogu sekwencji używa **__LOCAL_SIZE** w sekwencji prologu:

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje Naked](../c-language/naked-functions.md)
