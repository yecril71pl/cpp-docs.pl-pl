---
title: 'Deklarator odwołania do wartości: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 7710b6f1efc2de770b26ad50923bde2ee5200f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209557"
---
# <a name="lvalue-reference-declarator-amp"></a>Deklarator odwołania do wartości: &amp;

Przechowuje adres obiektu, ale składniowo zachowuje się jak obiekt.

## <a name="syntax"></a>Składnia

```
type-id & cast-expression
```

## <a name="remarks"></a>Uwagi

Odwołanie lvalue można traktować jako inną nazwę dla obiektu. Deklaracja odwołania wartościowanego lewostronnie składa się z opcjonalną listę specyfikatorów następuje deklarator odwołania. Odwołanie musi zostać zainicjowany i nie można jej zmienić.

Można też przekonwertować dowolnego obiektu, którego adres można przekonwertować na typ wskaźnika danego podobne typem odwołania. Na przykład dowolnego obiektu, którego adres można przekonwertować na typ `char *` można też przekonwertować na typ `char &`.

Nie należy mylić deklaracje odwołania przy użyciu [operatora address-of](../cpp/address-of-operator-amp.md). Gdy `&` *identyfikator* jest poprzedzony przez typ, takich jak **int** lub **char**, *identyfikator* jest zadeklarowany jako odwołanie do Typ. Gdy `&` *identyfikator* nie jest poprzedzony przez typ, użycie jest operator address-of.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano deklarator odwołania do przez zadeklarowanie `Person` obiektu i odwołanie do tego obiektu. Ponieważ `rFriend` jest odwołaniem do `myFriend`, aktualizowanie albo zmiennej zmiany tego samego obiektu.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Odwołania](../cpp/references-cpp.md)<br/>
[Argumenty funkcji będące odwołaniami](../cpp/reference-type-function-arguments.md)<br/>
[Wartości zwracane przez funkcje będące odwołaniami](../cpp/reference-type-function-returns.md)<br/>
[Odwołania do wskaźników](../cpp/references-to-pointers.md)