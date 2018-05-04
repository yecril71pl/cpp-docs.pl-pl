---
title: alignof i alignas (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2988d1260cac91e2614765aba8ae1b9be9b922
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="alignof-and-alignas-c"></a>alignof i alignas (C++)
`alignas` Specyfikatora typu jest przenośny, C++ standardowy sposób Określanie wyrównania niestandardowych zmiennych i typów zdefiniowanych przez użytkownika. `alignof` Operator jest również standardowe, przenośne sposobem uzyskania wyrównania określonego typu lub zmiennej.  
  
## <a name="example"></a>Przykład  
 Można użyć `alignas` na klasie uderzeniu lub union, lub na poszczególne elementy. Gdy wiele `alignas` specyfikatory zostaną napotkane, kompilator wybierze najbardziej rygorystyczne nich (jeden o największej wartości).  
  
```cpp  
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  

int main()
{  
    std::cout << alignof(Bar) << std::endl; // output: 16  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównanie](../cpp/alignment-cpp-declarations.md)