---
title: reinterpret_cast Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0957a696d7675a932aa86531d39f2e4895ba1ff9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reinterpretcast-operator"></a>Operator reinterpret_cast
Umożliwia żadnych wskaźnika do przekonwertowania na inny typ wskaźnika. Umożliwia także dowolnego typu całkowitego ma zostać przekonwertowany do dowolnego typu wskaźnika i na odwrót.  
  
## <a name="syntax"></a>Składnia  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Uwagi  
 Nieprawidłowe użycie `reinterpret_cast` łatwo operator może być niebezpieczne. Chyba, że żądane konwersja jest z założenia niskiego poziomu, należy użyć jednej z innych operatory rzutowania.  
  
 `reinterpret_cast` Operator może służyć do konwersji takich jak `char*` do `int*`, lub `One_class*` do `Unrelated_class*`, które są z założenia niebezpieczne.  
  
 Wynik `reinterpret_cast` bezpiecznie nie można użyć do wszelkich innych niż jest rzutowany jego oryginalnego typu. Innych celów są, co najlepiej nonportable.  
  
 `reinterpret_cast` Operatora nie można rzutować optymalizacji **const**, `volatile`, lub **__unaligned** atrybutów. Zobacz [const_cast Operator](../cpp/const-cast-operator.md) informacji o usuwaniu te atrybuty.  
  
 `reinterpret_cast` Operator konwertuje wartość wskaźnika o wartości null na wartość pustego wskaźnika typu docelowego.  
  
 Jeden praktyczne wykorzystanie `reinterpret_cast` znajduje się w funkcji skrótu, zmapowanym wartość do indeksu w taki sposób, że dwa różne wartości rzadko zakończenia się o tym samym indeksie.  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` Umożliwia wskaźnika powinien być traktowany jako typ całkowity. Wynik jest następnie bit przesunięte i XORed ze sobą, aby wygenerować unikatowego indeksu (unikatowe wysokiego stopnia prawdopodobieństwa). Indeks jest następnie obcięty przez standardowe C-styl rzutowany na typ zwracany funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory rzutowania](../cpp/casting-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)