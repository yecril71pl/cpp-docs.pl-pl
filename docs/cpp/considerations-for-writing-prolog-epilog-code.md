---
title: Zagadnienia dotyczące pisania kodu prologu/epilogu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cb66865d40e101f951b64aef07c0bb312f91611
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117572"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu

**Microsoft Specific**

Przed napisaniem własnej sekwencji kodu prologu i epilogu należy zrozumieć ułożenie ramki stosu. Warto też wiedzieć, jak używać `__LOCAL_SIZE` symboli.

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Układ ramki stosu

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

Stos zawsze powiększa się w dół (od najwyższego do najniższego adresu pamięci). Podstawowy wskaźnik (`ebp`) wskazuje na umieszczoną wartość `ebp`. Obszar zmiennych lokalnych rozpoczyna się od `ebp-4`. Aby uzyskać dostęp do zmiennych lokalnych, należy obliczyć przesunięcie z `ebp` przez odjęcie odpowiedniej wartości od `ebp`.

##  <a name="_pluslang___local_size"></a> __LOCAL_SIZE

Kompilator zapewnia symbol, `__LOCAL_SIZE`, do użycia w bloku asemblera wbudowanego w kodzie prologu funkcji. Ten symbol jest używany do alokowania miejsca dla zmiennych lokalnych na ramce stosu w niestandardowym kodzie prologu.

Kompilator określa wartość `__LOCAL_SIZE`. Jego wartość to całkowita liczba bajtów wszystkich zmiennych lokalnych zdefiniowanych przez użytkownika i zmiennych tymczasowych wygenerowanych przez kompilator. `__LOCAL_SIZE` może być używana tylko jako bezpośredni argument; Nie można użyć w wyrażeniu. Nie musisz zmienić lub ponownie definiować wartości tego symbolu. Na przykład:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Poniższy przykład funkcji "naked", zawierający niestandardową sekwencję prologu i epilogu sekwencji używa `__LOCAL_SIZE` symboli w sekwencji prologu:

```
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wywołania funkcji Naked](../cpp/naked-function-calls.md)