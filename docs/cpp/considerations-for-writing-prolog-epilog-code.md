---
title: Zagadnienia dotyczące pisania kodu prologu epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: a598ddbdd1b5f91c97e32905202e264b444c05d0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988702"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu

**Microsoft Specific**

Przed zapisaniem własnych sekwencji kodu prologu i epilogu ważne jest, aby zrozumieć, jak Ramka stosu jest rozłożone. Warto również wiedzieć, jak używać symbolu `__LOCAL_SIZE`.

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Układ ramki stosu

W tym przykładzie pokazano standardowy kod prologu, który może pojawić się w 32-bitowej funkcji:

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

Zmienna `localbytes` reprezentuje liczbę bajtów potrzebnych na stosie dla zmiennych lokalnych a zmienna `<registers>` jest symbolem zastępczym reprezentującym listę rejestrów, które mają być zapisane na stosie. Po umieszczeniu rejestrów na stosie, można tam umieścić wszelkie inne dane. Poniżej przedstawiono odpowiadający kod epilogu:

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

Stos zawsze powiększa się w dół (od najwyższego do najniższego adresu pamięci). Podstawowy wskaźnik (`ebp`) wskazuje na umieszczoną wartość `ebp`. Obszar zmiennych lokalnych rozpoczyna się o `ebp-4`. Aby uzyskać dostęp do zmiennych lokalnych, należy obliczyć przesunięcie z `ebp` przez odjęcie odpowiedniej wartości od `ebp`.

##  <a name="_pluslang___local_size"></a>__LOCAL_SIZE

Kompilator udostępnia symbol `__LOCAL_SIZE`, do użycia w bloku asemblera wbudowanego kodu prologu funkcji. Ten symbol służy do przydzielania przestrzeni dla zmiennych lokalnych w ramce stosu w niestandardowym kodzie prologu.

Kompilator określa wartość `__LOCAL_SIZE`. Wartość jest całkowitą liczbą bajtów wszystkich zdefiniowanych przez użytkownika zmiennych lokalnych i zmiennych tymczasowych generowanych przez kompilator. `__LOCAL_SIZE` można używać tylko jako bezpośredniego operandu; nie można jej użyć w wyrażeniu. Nie należy zmieniać ani ponownie definiować wartości tego symbolu. Na przykład:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Poniższy przykład funkcji owies, która zawiera niestandardowe wartości prologu i sekwencji epilogu używa symbolu `__LOCAL_SIZE` w sekwencji prologu:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wywołania funkcji Naked](../cpp/naked-function-calls.md)
