---
title: Zagadnienia dotyczące pisania kodu prologu/epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: cda6a6c82efcf30a916aced121024095d7ce8138
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337109"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu

**Specyficzne dla firmy Microsoft**

Przed napisaniem własnych sekwencji kodu prologu i epilogu, ważne jest, aby zrozumieć, jak ramka stosu jest rozmieszczona. Warto również wiedzieć, jak używać `__LOCAL_SIZE` symbolu.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Układ ramki stosu

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

Stos zawsze powiększa się w dół (od najwyższego do najniższego adresu pamięci). Podstawowy wskaźnik (`ebp`) wskazuje na umieszczoną wartość `ebp`. Obszar mieszkańców zaczyna `ebp-4`się od . Aby uzyskać dostęp do zmiennych lokalnych, należy obliczyć przesunięcie z `ebp` przez odjęcie odpowiedniej wartości od `ebp`.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a>__LOCAL_SIZE

Kompilator zawiera symbol, `__LOCAL_SIZE`do użytku w bloku asemblera wbudowanego kodu prologu funkcji. Ten symbol jest używany do przydzielania miejsca dla zmiennych lokalnych w ramce stosu w niestandardowym kodzie prologu.

Kompilator określa wartość `__LOCAL_SIZE`. . Jego wartość jest całkowita liczba bajtów wszystkich zmiennych lokalnych zdefiniowanych przez użytkownika i kompilator generowane zmienne tymczasowe. `__LOCAL_SIZE`może być używany tylko jako natychmiastowy operand; nie można go używać w wyrażeniu. Nie wolno zmieniać ani ponownie definiować wartości tego symbolu. Przykład:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Poniższy przykład nagiej funkcji zawierającej niestandardowe sekwencje `__LOCAL_SIZE` prologu i epilogu używa symbolu w sekwencji prologu:

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

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Wywołania funkcji Naked](../cpp/naked-function-calls.md)
