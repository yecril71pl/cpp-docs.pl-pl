---
title: 'Lvalue Reference deklarator: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 595f2b683d2abb4cdc8a328dc6e86338ab90f214
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178070"
---
# <a name="lvalue-reference-declarator-amp"></a>Lvalue Reference deklarator: &amp;

Przechowuje adres obiektu, ale zachowuje się syntaktycznie jak obiekt.

## <a name="syntax"></a>Składnia

```
type-id & cast-expression
```

## <a name="remarks"></a>Uwagi

Odwołanie lvalue można traktować jako inną nazwę obiektu. Deklaracja odwołania lvalue składa się z opcjonalnej listy specyfikatorów, a następnie odwołania deklarator. Odwołanie musi być zainicjowane i nie można go zmienić.

Każdy obiekt, którego adres można przekonwertować na dany typ wskaźnika, można również przekonwertować na podobny typ odwołania. Na przykład, każdy obiekt, którego adres można przekonwertować na typ `char *`, może być również konwertowany na typ `char &`.

Nie należy mylić deklaracji odwołań z użyciem [operatora address-of](../cpp/address-of-operator-amp.md). Gdy *identyfikator* `&`jest poprzedzony typem, takim jak **int** lub **char**, *Identyfikator* jest zadeklarowany jako odwołanie do typu. Gdy *identyfikator* `&`nie jest poprzedzony typem, użycie jest zgodne z operatorem address-of.

## <a name="example"></a>Przykład

Poniższy przykład demonstruje odwołanie deklarator przez zadeklarowanie obiektu `Person` i odwołania do tego obiektu. Ponieważ `rFriend` jest odwołaniem do `myFriend`, aktualizowanie każdej zmiennej zmienia ten sam obiekt.

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

## <a name="see-also"></a>Zobacz też

[Odwołania](../cpp/references-cpp.md)<br/>
[Argumenty funkcji będące odwołaniami](../cpp/reference-type-function-arguments.md)<br/>
[Wartości zwracane przez funkcje będące odwołaniami](../cpp/reference-type-function-returns.md)<br/>
[Odwołania do wskaźników](../cpp/references-to-pointers.md)
