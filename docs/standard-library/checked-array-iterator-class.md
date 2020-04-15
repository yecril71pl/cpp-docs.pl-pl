---
title: checked_array_iterator — Klasa
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: f177a45e700ab15852cd9c6d947873d247cf3828
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363867"
---
# <a name="checked_array_iterator-class"></a>checked_array_iterator — Klasa

Klasa `checked_array_iterator` umożliwia przekształcenie tablicy lub wskaźnika w kontrolerze. Ta klasa służy jako otoki (przy użyciu funkcji [make_checked_array_iterator)](../standard-library/iterator-functions.md#make_checked_array_iterator) dla nieprzetworzonych wskaźników lub tablic jako ukierunkowanego sposobu, aby zapewnić sprawdzanie i zarządzać niesprawdzonymi ostrzeżeniami wskaźnika zamiast globalnie wyciszania tych ostrzeżeń. W razie potrzeby można użyć niezaznaczonejednoznanej wersji tej klasy, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Ta klasa jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft. Aby uzyskać przykład pokazujący sposób pisania kodu, który nie wymaga użycia tej klasy, zobacz drugi przykład poniżej.

## <a name="syntax"></a>Składnia

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Uwagi

Ta klasa jest zdefiniowana w obszarze nazw [stdext.](../standard-library/stdext-namespace.md)

Aby uzyskać więcej informacji i przykładowy kod na temat funkcji kontrolera, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zdefiniować i zastosować sprawdzony iterator tablicy.

Jeśli miejsce docelowe nie jest wystarczająco duże, aby pomieścić wszystkie kopiowane elementy, tak jak byłoby w przypadku zmiany wiersza:

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

na

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

Wystąpi błąd w czasie wykonywania.

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>Przykład

Aby uniknąć konieczności `checked_array_iterator` klasy podczas korzystania z algorytmów biblioteki `vector` standardowej języka C++, należy rozważyć użycie zamiast tablicy dynamicznie przydzielone. Poniższy przykład demonstruje, jak to zrobić.

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Checked_array_iterator](#checked_array_iterator)|Tworzy domyślne `checked_array_iterator` lub `checked_array_iterator` z podstawowego iteratora.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ, który zapewnia różnicę `checked_array_iterator`między dwoma s odnoszących się do elementów w tym samym kontenerze.|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do elementu `checked_array_iterator`skierowanego przez .|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `checked_array_iterator`skierowanego przez .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[base](#base)|Odzyskuje podstawowego iteratora z jego `checked_array_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](#op_eq_eq)|Testy `checked_array_iterator`dwa s dla równości.|
|[operator!=](#op_neq)|Testy `checked_array_iterator`dwa s dla nierówności.|
|[<operatora](#op_lt)|Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest `checked_array_iterator` mniejsza niż po prawej stronie.|
|[>operatora](#op_gt)|Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest `checked_array_iterator` większa niż po prawej stronie.|
|[<operatora =](#op_lt_eq)|Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest mniejsza `checked_array_iterator` lub równa po prawej stronie.|
|[>operatora =](#op_gt_eq)|Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest większa `checked_array_iterator` lub równa po prawej stronie.|
|[operator*](#op_star)|Zwraca element, `checked_array_iterator` który adresuje.|
|[operator->](#op_arrow)|Zwraca wskaźnik do elementu adresowane przez `checked_array_iterator`.|
|[operator++](#op_add_add)|Zwiększa do `checked_array_iterator` następnego elementu.|
|[operator --](#operator--)|Zmniejsza do `checked_array_iterator` poprzedniego elementu.|
|[operator+=](#op_add_eq)|Dodaje określone przesunięcie `checked_array_iterator`do .|
|[operator+](#op_add)|Dodaje przesunięcie do iteratora i `checked_array_iterator` zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.|
|[operator-=](#operator-_eq)|Zmniejsza określone przesunięcie od `checked_array_iterator`.|
|[operator-](#operator-)|Zmniejsza odsunięcie od iteratora `checked_array_iterator` i zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.|
|[&#91;&#93;operatora](#op_at)|Zwraca odwołanie do elementu odsuniętego `checked_array_iterator` od elementu adresowane przez określoną liczbę pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Obszar nazw:** stdext

## <a name="checked_array_iteratorbase"></a><a name="base"></a>checked_array_iterator::base

Odzyskuje podstawowego iteratora z jego `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iteratorchecked_array_iterator"></a><a name="checked_array_iterator"></a>checked_array_iterator::checked_array_iterator

Tworzy domyślne `checked_array_iterator` lub `checked_array _iterator` z podstawowego iteratora.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Wskaźnik do tablicy.

*Rozmiar*\
Rozmiar tablicy.

*Indeks*\
(Opcjonalnie) Element w tablicy, aby zainicjować iteratora.  Domyślnie iterator jest inicjowany do pierwszego elementu w tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="checked_array_iteratordifference_type"></a><a name="difference_type"></a>checked_array_iterator::d00_typ

Typ, który zapewnia różnicę `checked_array_iterator`między dwoma s odnoszących się do elementów w tym samym kontenerze.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ `checked_array_iterator` różnicy jest taki sam jak typ różnicy iteratora.

Zobacz [checked_array_iterator::operator[]](#op_at) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_eq_eq"></a>checked_array_iterator::operator==

Testy `checked_array_iterator`dwa s dla równości.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Przeciw `checked_array_iterator` którym należy sprawdzić równość.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_neq"></a>checked_array_iterator::operator!=

Testy `checked_array_iterator`dwa s dla nierówności.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Przeciw `checked_array_iterator` którym należy sprawdzić, czy nie ma nierówności.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt"></a>checked_array_iterator::operator&lt;

Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest `checked_array_iterator` mniejsza niż po prawej stronie.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Przeciw `checked_array_iterator` którym należy sprawdzić, czy nie ma nierówności.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt"></a>checked_array_iterator::operator&gt;

Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest `checked_array_iterator` większa niż po prawej stronie.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Dla `checked_array_iterator` porównania.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator&lt; ](#op_lt) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt_eq"></a>checked_array_iterator::operator&lt;=

Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest mniejsza `checked_array_iterator` lub równa po prawej stronie.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Dla `checked_array_iterator` porównania.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator&gt; ](#op_gt_eq) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt_eq"></a>checked_array_iterator::operator&gt;=

Sprawdza, `checked_array_iterator` czy po lewej stronie operatora jest większa `checked_array_iterator` lub równa po prawej stronie.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Dla `checked_array_iterator` porównania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_star"></a>checked_array_iterator::operator*

Zwraca element, `checked_array_iterator` który adresuje.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego `checked_array_iterator`odnosi się .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="checked_array_iteratoroperator-gt"></a><a name="op_arrow"></a>checked_array_iterator::operator-&gt;

Zwraca wskaźnik do elementu adresowane przez `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu adresowane `checked_array_iterator`przez .

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::pointer](#pointer) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_add_add"></a>checked_array_iterator::operator++

Zwiększa do `checked_array_iterator` następnego elementu.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wstępnie z `checked_array_iterator` góry, a drugi, operator postincrement, zwraca kopię `checked_array_iterator`przyrostu .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
77
*/
```

## <a name="checked_array_iteratoroperator--"></a><a name="operator--"></a>checked_array_iterator::operator--

Zmniejsza do `checked_array_iterator` poprzedniego elementu.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wstępnie zdekralizowanym, `checked_array_iterator` a drugi operator postdekreacji zwraca `checked_array_iterator`kopię zdemprokowanego .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
6
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add_eq"></a>checked_array_iterator::operator+=

Dodaje określone przesunięcie `checked_array_iterator`do .

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, o które należy zwiększać iteratora.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do `checked_array_iterator`którego odnosi się .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add"></a>checked_array_iterator::operator+

Dodaje przesunięcie do iteratora i `checked_array_iterator` zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, które ma `checked_array_iterator`zostać dodane do .

### <a name="return-value"></a>Wartość zwracana

Adresowanie `checked_array_iterator` elementu odsunięcia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-_eq"></a>checked_array_iterator::operator-=

Zmniejsza określone przesunięcie od `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, o które należy zwiększać iteratora.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do `checked_array_iterator`którego odnosi się .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
/* Output:
199
3
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-"></a>checked_array_iterator::operator-

Zmniejsza odsunięcie od iteratora `checked_array_iterator` i zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, które ma zostać zniwelowane z . `checked_array_iterator`

### <a name="return-value"></a>Wartość zwracana

Adresowanie `checked_array_iterator` elementu odsunięcia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_at"></a>checked_array_iterator::operator[]

Zwraca odwołanie do elementu odsuniętego `checked_array_iterator` od elementu adresowane przez określoną liczbę pozycji.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie od `checked_array_iterator` adresu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do odsunięcia elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
/* Output:
3
*/
```

## <a name="checked_array_iteratorpointer"></a><a name="pointer"></a>checked_array_iterator::pointer

Typ, który zapewnia wskaźnik do elementu `checked_array_iterator`skierowanego przez .

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator*](#op_star) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratorreference"></a><a name="reference"></a>checked_array_iterator::odwołanie

Typ, który zawiera odwołanie do elementu `checked_array_iterator`skierowanego przez .

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator[]](#op_at) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
