---
title: "iterator_traits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::iterator_traits
dev_langs: C++
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ac3034f1384bbd38cb0ca90d0df8ff5bed411d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iteratortraits-struct"></a>iterator_traits — Struktura
Struktura pomocnika szablon używany do określenia wszystkich definicji typu krytycznego mających iteratora.  
  
## <a name="syntax"></a>Składnia  

```    
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
 Struktura szablonu określa typy elementów członkowskich  
  
- **iterator_category**: synonimem **Iterator::iterator_category**.  
  
- `value_type`: synonimem **Iterator::value_type**.  
  
- `difference_type`: synonimem **Iterator::difference_type**.  
  
- `distance_type`: synonimem **Iterator::difference_type.**  
  
- **wskaźnik**: synonimem **Iterator::pointer**.  
  
- **Odwołanie**: synonimem **Iterator::reference**.  
  
 Częściowe specjalizacje określić typy krytyczne skojarzone z wskaźnik do obiektu typu **typu \***  lub const **typu \*** .  
  
 W tej implementacji, które umożliwia także kilka funkcji szablonów, które nie korzystać z częściowa specjalizacja:  
  
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
  
 te określają, niektóre z takich samych typach więcej pośrednio. Jako argumentów w wywołaniu funkcji korzystania z tych funkcji. Ich jedynym celem jest podać parametr klasy szablonu przydatne do wywołanej funkcji.  
  
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
\* Output:   
struct std::random_access_iterator_tag  
a a a a a a a a a a   
struct std::bidirectional_iterator_tag  
0 0 0 0 0 0 0 0 0 0   
*\  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



