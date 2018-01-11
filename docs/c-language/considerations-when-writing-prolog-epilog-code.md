---
title: "Zagadnienia dotyczące pisania kodu prologu epilogu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01a153011ad0cd571762c6473f6121a55045396c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="considerations-when-writing-prologepilog-code"></a>Zagadnienia dotyczące pisania kodu prologu/epilogu
**Dotyczące firmy Microsoft**  
  
 Przed napisaniem własnej sekwencji kodu prologu i epilogu należy zrozumieć ułożenie ramki stosu. Warto również wiedzieć, jak używać **__local_size —** stała wstępnie zdefiniowane.  
  
##  <a name="_clang_c_stack_frame_layout"></a>C — ramka stosu — układ  
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
  
##  <a name="_clang_the___local_size_constant"></a>__Local_size — stała  
 Kompilator zapewnia stałą, **__local_size —**, do użycia w bloku asemblera wbudowanego kodu prologu funkcji. Stała jest używana do alokowania miejsca dla zmiennych lokalnych na ramce stosu w niestandardowym kodzie prologu.  
  
 Kompilator określa wartość **__local_size —**. Wartość to całkowita liczba bajtów wszystkich zmiennych lokalnych zdefiniowanych przez użytkownika i zmiennych tymczasowych wygenerowanych przez kompilator. **__Local_size —** mogą być używane tylko jako argumentu natychmiastowego; nie można użyć w wyrażeniu. Nie wolno zmieniać lub ponownie definiować wartości tej stałej. Na przykład:  
  
```  
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov      eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 Poniższy przykład przedstawia funkcji naked zawierający niestandardowe prolog i epilog sekwencji używa **__local_size —** w prologu sekwencji:  
  
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
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Naked](../c-language/naked-functions.md)