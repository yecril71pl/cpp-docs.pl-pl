---
title: "Operator bezpośredni: * | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c87c279ae1f45899dfa4525c3bdc65bfa5acc2c
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="indirection-operator-"></a>Operator bezpośredni: *
## <a name="syntax"></a>Składnia  
  
```  
  
* cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowy operator pośredni (**\***) wyłuskań wskaźnika; oznacza to, konwertuje wartość wskaźnika na l wartość. Argument operacji operatora pośredni musi być wskaźnikiem do typu. Wynik wyrażenia pośredni jest typu, z którego pochodzi typu wskaźnika. Korzystanie z  **\***  operatora w tym kontekście różni się od jego znaczenie jako operator binarny, który jest mnożenia.  
  
 Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Jeśli wskazuje on lokalizację magazynu, wynikiem jest l-wartość opisująca lokalizację magazynu.  
  
 Operator pośredni pozwala zbiorczo usunąć odwołania do wskaźników do wskaźników. Na przykład:  
  
```  
// expre_Indirection_Operator.cpp  
// compile with: /EHsc  
// Demonstrate indirection operator  
#include <iostream>  
using namespace std;  
int main() {  
   int n = 5;  
   int *pn = &n;  
   int **ppn = &pn;  
  
   cout  << "Value of n:\n"  
         << "direct value: " << n << endl  
         << "indirect value: " << *pn << endl  
         << "doubly indirect value: " << **ppn << endl  
         << "address of n: " << pn << endl  
         << "address of n via indirection: " << *ppn << endl;  
}  
```  
  
 Jeśli wartość wskaźnika jest nieprawidłowy, wynikiem jest niezdefiniowany. Następująca lista zawiera niektóre z najbardziej typowych warunków, które unieważniają wartość wskaźnika.  
  
-   Wskaźnik jest pustym wskaźnikiem.  
  
-   Wskaźnik określa adres lokalnego elementu, który nie jest widoczny w momencie odwołania.  
  
-   Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.  
  
-   Wskaźnik określa adres nieużywany przez program wykonujący.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operator Address-of: &](../cpp/address-of-operator-amp.md)   
 [Operatory pośrednie i „Address-of”](../c-language/indirection-and-address-of-operators.md)