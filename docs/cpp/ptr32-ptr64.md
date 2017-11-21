---
title: __ptr32 i __ptr64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs: C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f70de0e9e7bc9c698010e7378c705789d380ed6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__ptr32`reprezentuje wskaźnik natywny w systemie 32-bitowy, podczas gdy `__ptr64` reprezentuje wskaźnik natywny w 64-bitowym systemie.  
  
 Poniższy przykład przedstawia sposób zadeklarować każdego z tych typów wskaźnika:  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 W systemie 32-bitowy, wskaźnik zadeklarowana z `__ptr64` został obcięty do wskaźnika 32-bitowych. W systemie 64-bitowym, wskaźnik zadeklarowana z `__ptr32` jest traktowany jak wskaźnik 64-bitowych.  
  
> [!NOTE]
>  Nie można użyć `__ptr32` lub `__ptr64` podczas kompilowania za pomocą **/CLR: pure**. W przeciwnym razie `Compiler Error C2472` zostanie wygenerowany. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można zadeklarować i przydzielić wskaźników za pomocą `__ptr32` i `__ptr64` słów kluczowych.  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
```Output  
32  
64  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)