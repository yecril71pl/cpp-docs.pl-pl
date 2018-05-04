---
title: Na podstawie wskaźników (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __based
- __based_cpp
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6cc2e45574d30ae1a544da78a4f7a75321a1156
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C++)
**Microsoft Specific**  
  
 `__based` — Słowo kluczowe umożliwia zadeklarować wskaźniki oparte na wskaźnikach (wskaźniki, które są przesunięciami z istniejących wskaźniki).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
type __based( base ) declarator   
```  
  
## <a name="remarks"></a>Uwagi  
 Wskaźniki oparte na adresach wskaźnika są jedynymi `__based` — słowo kluczowe prawidłowy w kompilacjach kodu 32-bitowy lub 64-bitowej. Kompilator Microsoft 32-bitowa C/C++ wskaźnik bazowy jest 32-bitowego przesunięcia z 32-bitowych wskaźnik podstawowy. Podobne ograniczeń przechowuje w środowiskach, 64-bitowy, gdzie wskaźnik bazowy jest offset 64-bitowym z base 64-bitowych.  
  
 Jeden na użytek wskaźniki oparte na wskaźnikach jest trwały identyfikatorów, które zawierają wskaźniki. Listy połączonej, która składa się z wskaźniki oparte na wskaźnik można można zapisywane na dysku, a następnie ponownie załadować do innego miejsca w pamięci, za pomocą wskaźniki pozostałych prawidłowe. Na przykład:  
  
```  
// based_pointers1.cpp  
// compile with: /c  
void *vpBuffer;  
struct llist_t {  
   void __based( vpBuffer ) *vpData;  
   struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 Wskaźnik `vpBuffer` ma przypisany adres pamięci przydzielonej w pewnym momencie nowsze w programie. Listy połączonej został przeniesiony z uwzględnieniem wartości `vpBuffer`.  
  
> [!NOTE]
>  Utrwalanie identyfikatory zawierające wskaźniki może być również wykonywane przy użyciu [plików mapowanych na pamięć](http://msdn.microsoft.com/library/windows/desktop/aa366556).  
  
 Podczas usuwania odwołania wskaźnik bazowy, podstawowym musi być jawnie określony lub niejawnie znany za pomocą deklaracji.  
  
 Zgodność z poprzednimi wersjami **_based** jest synonimem `__based`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje, zmiana wskaźnik bazowy przez zmianę jego elementów bazowych.  
  
```  
// based_pointers2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int a1[] = { 1,2,3 };  
int a2[] = { 10,11,12 };  
int *pBased;  
  
typedef int __based(pBased) * pBasedPtr;  
  
using namespace std;  
int main() {  
   pBased = &a1[0];  
   pBasedPtr pb = 0;  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
  
   pBased = &a2[0];  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
}  
```  
  
```Output  
1  
2  
10  
11  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../cpp/keywords-cpp.md)   
 [alloc_text](../preprocessor/alloc-text.md)