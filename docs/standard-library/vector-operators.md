---
title: Operatory&gt; &lt;Vector
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
ms.openlocfilehash: f6717add93c489f536bd0c0b0f82b74bbd915985
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876064"
---
# <a name="ltvectorgt-operators"></a>Operatory&gt; &lt;Vector

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli wektory nie są równe; **Fałsz** , jeśli wektory są równe.

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

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt po lewej stronie operatora jest mniejszy od obiektu po prawej stronie.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli wektor po lewej stronie operatora jest mniejszy od wektora po prawej stronie operatora; w przeciwnym razie **false**.

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

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt po lewej stronie operatora jest mniejszy od lub równy obiektowi po prawej stronie.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli wektor po lewej stronie operatora jest mniejszy lub równy wektorowi po prawej stronie operatora; w przeciwnym razie **false**.

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

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli wektor po lewej stronie operatora jest równy wektorowi po prawej stronie operatora; w przeciwnym razie **false**.

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

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli wektor po lewej stronie operatora jest większy niż wektor po prawej stronie operatora; w przeciwnym razie **false**.

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

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt po lewej stronie operatora jest większy niż lub równy obiektowi po prawej stronie.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `vector`.

*prawa*\
Obiekt typu `vector`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli wektor po lewej stronie operatora jest większy niż lub równy wektorowi po prawej stronie wektora; w przeciwnym razie **false**.

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
