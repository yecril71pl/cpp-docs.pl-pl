---
title: iterator_traits — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator_traits
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
ms.openlocfilehash: 924ca5ae1d32753bbe315252d942425712962639
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689448"
---
# <a name="iterator_traits-struct"></a>iterator_traits — Struktura

Struktura pomocnika szablonu używana do określania wszystkich definicji typu krytycznego, które powinny mieć iterator.

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

Struktura szablonu definiuje typy elementów członkowskich

- `iterator_category`: synonim `Iterator::iterator_category`.

- `value_type`: synonim `Iterator::value_type`.

- `difference_type`: synonim `Iterator::difference_type`.

- `distance_type`: synonim dla `Iterator::difference_type.`

- `pointer`: synonim `Iterator::pointer`.

- `reference`: synonim `Iterator::reference`.

Częściowe specjalizacje określają typy krytyczne skojarzone ze wskaźnikiem **obiektu typu** <strong>\*</strong> lub **typu const** <strong>\*</strong>.

W tej implementacji można także użyć kilku funkcji szablonu, które nie używają częściowej specjalizacji:

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

co bardziej pośrednio określa kilka typów tego samego typu. Te funkcje są używane jako argumenty wywołania funkcji. Ich jedynym celem jest dostarczenie użytecznego parametru szablonu klasy do wywołanej funkcji.

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<iterator >](../standard-library/iterator.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
