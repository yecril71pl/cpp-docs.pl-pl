---
title: '&lt;Operatory wektorów &gt;'
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: 6e3b78a7b7176be917da5a3e44e9bf54efc0b08c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224542"
---
# <a name="ltvectorgt-operators"></a>&lt;Operatory wektorów &gt;

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektory nie są równe; **`false`** Jeśli wektory są równe.

### <a name="remarks"></a>Uwagi

Dwa wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy obiekt po lewej stronie operatora jest mniejszy od obiektu po prawej stronie.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor po lewej stronie operatora jest mniejszy od wektora po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy obiekt po lewej stronie operatora jest mniejszy od lub równy obiektowi po prawej stronie.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor po lewej stronie operatora jest mniejszy lub równy wektorowi po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor po lewej stronie operatora jest równy wektorowi po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Dwa wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Testuje, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor po lewej stronie operatora jest większy niż wektor po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy obiekt po lewej stronie operatora jest większy niż lub równy obiektowi po prawej stronie.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `vector`.

*Kliknij*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor po lewej stronie operatora jest większy niż lub równy wektorowi po prawej stronie wektora; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```
