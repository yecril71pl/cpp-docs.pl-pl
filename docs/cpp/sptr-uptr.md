---
title: Modyfikatory __sptr, __uptr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __uptr_cpp
- __sptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: daa431204c66def272d07fc0b670dc279e1569ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sptr-uptr"></a>__sptr, __uptr
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Należy użyć modyfikatora `__sptr` lub `__uptr` w deklaracji 32-bitowego wskaźnika do określenia, jak kompilator będzie konwertował wskaźnik 32-bitowy na wskaźnik 64-bitowy. Wskaźnik 32-bitowy jest konwertowany, na przykład gdy jest przypisany do zmiennej wskaźnika 64-bitowego lub wyłuskany na platformie 64-bitowej.  
  
 Dokumentacja obsługi technicznej Microsoft dla 64-bitowych platform czasami dotyczy najważniejszego bitu wskaźnika 32-bitowego, jako bitu znaku. Domyślnie kompilator używa rozszerzenia znaku, aby konwertować wskaźnik 32-bitowy na wskaźnik 64-bitowy. Oznacza to, że najmniej znaczące 32 bity wskaźnika 64-bitowego są ustawione na wartość wskaźnika 32-bitowego i najbardziej znaczące 32 bity są ustawione na wartość bitu znaku wskaźnika 32-bitowego. Ta konwersja daje poprawne wyniki, jeśli bit znaku ma wartość 0, ale nie jeśli bitem znaku jest 1. Na przykład 32-bitowy adres 0x7FFFFFFF daje równoważny 64-bitowy adres 0x000000007FFFFFFF, ale 32-bitowy adres 0x80000000 zostanie niepoprawnie zmieniony na 0xFFFFFFFF80000000.  
  
 Modyfikator `__sptr` lub wskaźnik oznaczony określa, że konwersja wskaźnika ustawia najbardziej znaczące bity wskaźnika 64-bitowego na bit znaku wskaźnika 32-bitowego. Modyfikator `__uptr` lub wskaźnik nieoznaczony określa, że konwersja ustawi najbardziej znaczące bity na wartość zero. Pokaż następujące deklaracje `__sptr` i `__uptr` Modyfikatory używane z dwóch niekwalifikowanych wskaźnikami, dwóch wskaźników kwalifikowany za pomocą [__ptr32](../cpp/ptr32-ptr64.md) typu, a parametr funkcji.  
  
```  
int * __sptr psp;  
int * __uptr pup;  
int * __ptr32 __sptr psp32;  
int * __ptr32 __uptr pup32;  
void MyFunction(char * __uptr __ptr32 myValue);  
```  
  
 Użycie modyfikatorów `__sptr` i `__uptr` z deklaracjami wskaźników. Używać modyfikatorów w pozycji [kwalifikator typu wskaźnika](../c-language/pointer-declarations.md), co oznacza, że modyfikator wykonaj gwiazdki. Nie można używać modyfikatorów z [wskaźników do elementów członkowskich](../cpp/pointers-to-members.md). Modyfikatory nie wpływają na deklaracje niewskaźnikowe.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie deklarowane są wskaźniki 32-bitowe, które używają modyfikatorów `__sptr` i `__uptr`, każdy 32-bitowy wskaźnik jest przypisywany do zmiennej wskaźnika 64-bitowego, a następnie wyświetlana jest wartość szesnastkowa każdego wskaźnika 64-bitowego. Przykład jest kompilowany za pomocą natywnego 64-bitowego kompilatora i jest wykonywany na platformie 64-bitowej.  
  
```cpp  
// sptr_uptr.cpp  
// processor: x64  
#include "stdio.h"  
  
int main()  
{  
    void *        __ptr64 p64;  
    void *        __ptr32 p32d; //default signed pointer  
    void * __sptr __ptr32 p32s; //explicit signed pointer  
    void * __uptr __ptr32 p32u; //explicit unsigned pointer  
  
// Set the 32-bit pointers to a value whose sign bit is 1.  
    p32d = reinterpret_cast<void *>(0x87654321);  
    p32s = p32d;  
    p32u = p32d;  
  
// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated   
// to the __sptr and __uptr modifiers.   
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");  
    printf("p32d:       %p\n", p32d);   
    printf("p32s:       %p\n", p32s);  
    printf("p32u:       %p\n", p32u);  
  
    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");  
    p64 = p32d;   
    printf("p32d: p64 = %p\n", p64);  
    p64 = p32s;  
    printf("p32s: p64 = %p\n", p64);  
    p64 = p32u;  
    printf("p32u: p64 = %p\n", p64);  
    return 0;  
}  
```  
  
```Output  
Display each 32-bit pointer (as an unsigned 64-bit pointer):  
p32d:       0000000087654321  
p32s:       0000000087654321  
p32u:       0000000087654321  
  
Display the 64-bit pointer created from each 32-bit pointer:  
p32d: p64 = FFFFFFFF87654321  
p32s: p64 = FFFFFFFF87654321  
p32u: p64 = 0000000087654321  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)