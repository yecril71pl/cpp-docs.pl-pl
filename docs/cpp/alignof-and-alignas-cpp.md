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
ms.openlocfilehash: c10821f7e71c928fa749c2b85bd076cb9af6d04a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402419"
---
# <a name="alignof-and-alignas-c"></a>alignof i alignas (C++)
**Alignas** Specyfikator typu jest przenośny, C++ standardowy sposób określić niestandardowe wyrównania zmiennych i typów zdefiniowanych przez użytkownika. **Alignof** operator podobnie jest standardowa, przenośne sposobem uzyskania wyrównanie określonego typu lub zmiennej.  
  
## <a name="example"></a>Przykład  
 Możesz użyć **alignas** na klasę uderzeniu lub Unii, lub na poszczególnych elementów członkowskich. Gdy wiele **alignas** specyfikatory zostaną napotkane, kompilator wybierze najbardziej rygorystyczne z nich (jedna o największej wartości).  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Wyrównanie](../cpp/alignment-cpp-declarations.md)