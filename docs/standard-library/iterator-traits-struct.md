---
title: iterator_traits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator_traits
dev_langs:
- C++
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb91bc7ec37d4738aaf9f1c7ac6532079a0b71d0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313733"
---
# <a name="iteratortraits-struct"></a>iterator_traits — Struktura

Struktura pomocnika szablonu używany do określenia wszystkich definicji typu krytycznego dla mających iterator.

## <a name="syntax"></a>Składnia

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>Uwagi

Struktura szablon definiuje typy elementów członkowskich

- `iterator_category`: jest to synonim `Iterator::iterator_category`.

- `value_type`: jest to synonim `Iterator::value_type`.

- `difference_type`: jest to synonim `Iterator::difference_type`.

- `distance_type`: jest to synonim `Iterator::difference_type.`

- `pointer`: jest to synonim `Iterator::pointer`.

- `reference`: jest to synonim `Iterator::reference`.

Częściowe specjalizacje określić typy krytyczne skojarzony wskaźnik do obiektu typu **typu** <strong>\*</strong> lub **typ const**  <strong>\*</strong>.

W tej implementacji, które można również użyć kilku funkcji szablonu, które nie należy wprowadzać użytkowania częściowej specjalizacji:

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

te określają kilka takich samych typach bardziej pośrednio. Te funkcje są używane jako argumentów w wywołaniu funkcji. Jedynym ich celem jest podać parametr klasy szablonu przydatne dla wywoływanej funkcji.

## <a name="example"></a>Przykład

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
/* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
