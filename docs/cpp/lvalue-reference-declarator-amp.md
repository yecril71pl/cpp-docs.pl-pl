---
title: "Deklarator odwołania do wartości: &amp; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bea07ed3139240279848d94184564ec821a8cd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lvalue-reference-declarator-amp"></a>Deklarator odwołania do wartości:&amp;
Przechowuje adres obiektu, ale składniowo zachowuje się jak obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
type-id & cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do wartości można traktować jako inną nazwę dla obiektu. Deklaracja odwołania l-wartością składa się z opcjonalną listę specyfikatory następuje deklarator odwołania. Odwołanie musi zostać zainicjowany i nie można zmienić.  
  
 Każdy obiekt, którego adres można przekonwertować na typ wskaźnika danego również można przekonwertować na podobny typ referencyjny. Na przykład dowolny obiekt, którego adres może być konwertowana na typ `char *` również można przekonwertować na typ `char &`.  
  
 Nie należy mylić deklaracje odwołanie z użyciem [operator address-of](../cpp/address-of-operator-amp.md). Gdy `&` *identyfikator* jest poprzedzony typu, takich jak `int` lub `char`, *identyfikator* jest zadeklarowany jako odwołanie do typu. Gdy `&` *identyfikator* nie jest poprzedzony przez typ, użycie, jest operator address-of.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano deklarator odwołania do przez zadeklarowanie `Person` obiektu i odwołania do tego obiektu. Ponieważ `rFriend` jest odwołaniem do `myFriend`, aktualizowania, albo zmiennej zmiany tego samego obiektu.  
  
```  
// reference_declarator.cpp  
// compile with: /EHsc  
// Demonstrates the reference declarator.  
#include <iostream>  
using namespace std;  
  
struct Person  
{  
    char* Name;  
    short Age;  
};  
  
int main()  
{  
   // Declare a Person object.  
   Person myFriend;  
  
   // Declare a reference to the Person object.  
   Person& rFriend = myFriend;  
  
   // Set the fields of the Person object.  
   // Updating either variable changes the same object.  
   myFriend.Name = "Bill";  
   rFriend.Age = 40;  
  
   // Print the fields of the Person object to the console.  
   cout << rFriend.Name << " is " << myFriend.Age << endl;  
}  
```  
  
```Output  
Bill is 40  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania](../cpp/references-cpp.md)   
 [Argumenty funkcji typu odwołania](../cpp/reference-type-function-arguments.md)   
 [Zwracanie funkcji typu odwołania](../cpp/reference-type-function-returns.md)   
 [Odwołania do wskaźników](../cpp/references-to-pointers.md)