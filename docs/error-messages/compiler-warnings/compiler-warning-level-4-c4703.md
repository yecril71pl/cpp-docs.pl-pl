---
title: "Kompilatora (poziom 4) ostrzeżenie C4703 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4703
dev_langs: C++
helpviewer_keywords: C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 995491fd4fdd05465b4ebdc961ad7ca09c4e7697
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4703"></a>Kompilator C4703 ostrzegawcze (poziom 4)
Potencjalnie odinicjowany lokalnej zmiennej wskaźnikowej "name" używane  
  
 Lokalnej zmiennej wskaźnikowej *nazwa* może być używany bez zostanie przypisana wartość. Może to spowodować nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje C4701 i C4703.  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 Aby usunąć to ostrzeżenie, zainicjować zmiennej, jak pokazano w poniższym przykładzie:  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator C4701 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [Ostrzeżenia, / SDL i poprawy niezainicjowanej zmiennej wykrywania](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)