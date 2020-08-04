---
title: length_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::length_error
helpviewer_keywords:
- length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
ms.openlocfilehash: 740ae69948a8f1975872f223ba51fb669121a891
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520891"
---
# <a name="length_error-class"></a>length_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłoszenia próby wygenerowania obiektu zbyt długo.

## <a name="syntax"></a>Składnia

```cpp
class length_error : public logic_error {
public:
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwracana przez `what()` to jest kopia `message.data()` . Aby uzyskać więcej informacji, zobacz [`what`](../standard-library/exception-class.md) i [`data`](../standard-library/basic-string-class.md#data) .

## <a name="example"></a>Przykład

```cpp
// length_error.cpp
// compile with: /EHsc /GR /MDd
#include <vector>
#include <iostream>

using namespace std;

template<class  T>
class stingyallocator : public allocator< T>
{
public:
   template <class U>
      struct rebind { typedef stingyallocator<U> other; };
   _SIZT max_size( ) const
   {
         return 10;
   };

};

int main( )
{
   try
   {
      vector<int, stingyallocator< int > > myv;
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught vector<T> too long
Type class std::length_error
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<stdexcept>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa logic_error](../standard-library/logic-error-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
