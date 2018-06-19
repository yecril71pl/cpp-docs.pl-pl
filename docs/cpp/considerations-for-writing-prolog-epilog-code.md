---
title: Zagadnienia dotyczące pisania kodu prologu epilogu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5bd87d4af4c797d324e6f882cc5c2e139a784543
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414773"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Przed napisaniem własnej sekwencji kodu prologu i epilogu należy zrozumieć ułożenie ramki stosu. Warto również wiedzieć, jak używać **__local_size —** symbolu.  
  
##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Ramka stosu — układ  
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
  
 Stos zawsze powiększa się w dół (od najwyższego do najniższego adresu pamięci). Podstawowy wskaźnik (`ebp`) wskazuje na umieszczoną wartość `ebp`. Zmienne lokalne obszaru zaczyna się od `ebp-4`. Aby uzyskać dostęp do zmiennych lokalnych, należy obliczyć przesunięcie z `ebp` przez odjęcie odpowiedniej wartości od `ebp`.  
  
##  <a name="_pluslang___local_size"></a> __LOCAL_SIZE —  
 Kompilator zawiera symbol, **__local_size —**, do użycia w bloku asemblera wbudowanego kodu prologu funkcji. Ten symbol jest używany do przydzielenia miejsca dla zmiennych lokalnych w ramce stosu w prologu niestandardowego kodu.  
  
 Kompilator określa wartość **__local_size —**. Wartość jest to całkowita liczba bajtów wszystkich zdefiniowanych przez użytkownika zmiennych lokalnych i generowane przez kompilator zmiennych tymczasowych. **__Local_size —** mogą być używane tylko jako argumentu natychmiastowego; nie można użyć w wyrażeniu. Nie musisz zmienić lub zmień definicję wartość tego symbolu. Na przykład:  
  
```  
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov        eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 Poniższy przykład przedstawia funkcji naked zawierający niestandardowe prolog i epilog sekwencji używa **__local_size —** symbol w prologu sekwencji:  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji Naked](../cpp/naked-function-calls.md)