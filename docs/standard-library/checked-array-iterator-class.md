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
ms.openlocfilehash: 467a94212d7b1e9d28a3229660b8a8619993b201
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684944"
---
# <a name="checked_array_iterator-class"></a>checked_array_iterator — Klasa

`checked_array_iterator`Klasa umożliwia przekształcenie tablicy lub wskaźnika w sprawdzony iterator. Ta klasa jest używana jako otoka (przy użyciu funkcji [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) ) dla surowych wskaźników lub tablic jako metoda dostosowana do zapewnienia kontroli i zarządzania ostrzeżeniami o niesprawdzonym wskaźniku zamiast globalnie wyciszania te ostrzeżenia. W razie potrzeby można użyć niesprawdzonej wersji tej klasy, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Ta klasa jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft. Aby uzyskać przykład pokazujący sposób pisania kodu, który nie wymaga użycia tej klasy, zobacz drugi przykład poniżej.

## <a name="syntax"></a>Składnia

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Uwagi

Ta klasa jest zdefiniowana w przestrzeni nazw [stdext](../standard-library/stdext-namespace.md) .

Aby uzyskać więcej informacji i przykładowego kodu w funkcji sprawdzonego iteratora, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak zdefiniować i zastosować sprawdzony iterator tablicy.

Jeśli miejsce docelowe nie jest wystarczająco duże, aby pomieścić wszystkie kopiowane elementy, tak jak byłoby w przypadku zmiany wiersza:

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

na wartość

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

Aby uniknąć konieczności stosowania `checked_array_iterator` klasy przy użyciu algorytmów standardowej biblioteki języka C++, należy rozważyć użycie `vector` zamiast dynamicznie przystosowanej tablicy. Poniższy przykład demonstruje, jak to zrobić.

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

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|Konstruuje wartość domyślną `checked_array_iterator` lub a `checked_array_iterator` z iteratora podstawowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma `checked_array_iterator` s odwołującymi się do elementów w tym samym kontenerze.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu, do którego odnosił się `checked_array_iterator` .|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu, do którego odnosi się `checked_array_iterator` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[base](#base)|Odzyskuje podstawowy iterator od jego `checked_array_iterator` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator = =](#op_eq_eq)|Testuje dwa `checked_array_iterator` s dla równości.|
|[operator! =](#op_neq)|Testuje dwa `checked_array_iterator` s na nierówność.|
|[<operatora ](#op_lt)|Testuje, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy od po `checked_array_iterator` prawej stronie.|
|[>operatora ](#op_gt)|Testuje, czy `checked_array_iterator` po lewej stronie operatora jest większy od po `checked_array_iterator` prawej stronie.|
|[<operatora =](#op_lt_eq)|Testuje, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy lub równy po `checked_array_iterator` prawej stronie.|
|[>operatora =](#op_gt_eq)|Testuje, czy `checked_array_iterator` po lewej stronie operatora jest większy niż lub równy po `checked_array_iterator` prawej stronie.|
|[zakład](#op_star)|Zwraca element, który jest `checked_array_iterator` adresem.|
|[operator — >](#op_arrow)|Zwraca wskaźnik do elementu, do którego odnosi się `checked_array_iterator` .|
|[operator + +](#op_add_add)|Zwiększa `checked_array_iterator` do następnego elementu.|
|[operator--](#operator--)|Zmniejsza `checked_array_iterator` do poprzedniego elementu.|
|[operator + =](#op_add_eq)|Dodaje określone przesunięcie do `checked_array_iterator` .|
|[operator +](#op_add)|Dodaje przesunięcie do iteratora i zwraca nowy odnoszący `checked_array_iterator` się do wstawionego elementu w nowym położeniu przesunięcia.|
|[operator-=](#operator-_eq)|Zmniejsza określone przesunięcie od `checked_array_iterator` .|
|[zakład](#operator-)|Zmniejsza przesunięcie od iteratora i zwraca nowy odnoszący `checked_array_iterator` się do wstawionego elementu w nowym położeniu przesunięcia.|
|[&#91;&#93;operatora ](#op_at)|Zwraca odwołanie do przesunięcia elementu z elementu, który jest adresowany przez `checked_array_iterator` określoną liczbę pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<iterator>

**Przestrzeń nazw:** stdext

## <a name="checked_array_iteratorbase"></a><a name="base"></a> checked_array_iterator:: Base

Odzyskuje podstawowy iterator od jego `checked_array_iterator` .

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratorchecked_array_iterator"></a><a name="checked_array_iterator"></a> checked_array_iterator:: checked_array_iterator

Konstruuje wartość domyślną `checked_array_iterator` lub a `checked_array _iterator` z iteratora podstawowego.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do tablicy.

*zmienia*\
Rozmiar tablicy.

*indeks*\
Obowiązkowe Element w tablicy, aby zainicjować iterator.  Domyślnie iterator jest inicjowany do pierwszego elementu w tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratordifference_type"></a><a name="difference_type"></a> checked_array_iterator::d ifference_type

Typ, który zawiera różnicę między dwoma `checked_array_iterator` s odwołującymi się do elementów w tym samym kontenerze.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`checked_array_iterator`Typ różnicy jest taki sam jak typ różnicy iteratora.

Aby uzyskać przykład kodu, zobacz [checked_array_iterator:: operator []](#op_at) .

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_eq_eq"></a> checked_array_iterator:: operator = =

Testuje dwa `checked_array_iterator` s dla równości.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`checked_array_iterator`Dla którego ma zostać sprawdzona równość.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator"></a><a name="op_neq"></a> checked_array_iterator:: operator! =

Testuje dwa `checked_array_iterator` s na nierówność.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Dla `checked_array_iterator` którego ma zostać wyszukana nierówność.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt"></a> checked_array_iterator:: operator&lt;

Testuje, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy od po `checked_array_iterator` prawej stronie.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Dla `checked_array_iterator` którego ma zostać wyszukana nierówność.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt"></a> checked_array_iterator:: operator&gt;

Testuje, czy `checked_array_iterator` po lewej stronie operatora jest większy od po `checked_array_iterator` prawej stronie.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`checked_array_iterator`Do porównania.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator:: operator &lt; ](#op_lt) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt_eq"></a> checked_array_iterator:: operator&lt;=

Testuje, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy lub równy po `checked_array_iterator` prawej stronie.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`checked_array_iterator`Do porównania.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator:: operator &gt; = ](#op_gt_eq) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt_eq"></a> checked_array_iterator:: operator&gt;=

Testuje, czy `checked_array_iterator` po lewej stronie operatora jest większy niż lub równy po `checked_array_iterator` prawej stronie.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`checked_array_iterator`Do porównania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator"></a><a name="op_star"></a> checked_array_iterator:: operator *

Zwraca element, który jest `checked_array_iterator` adresem.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego odnosi się `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator-gt"></a><a name="op_arrow"></a> checked_array_iterator:: operator-&gt;

Zwraca wskaźnik do elementu, do którego odnosi się `checked_array_iterator` .

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, do którego odnosił się `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::p ointer](#pointer) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_add_add"></a> checked_array_iterator:: operator + +

Zwiększa `checked_array_iterator` do następnego elementu.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wartości z przedziału, `checked_array_iterator` a drugi, operator postinkrementacji, zwraca kopię przyrostu `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator--"></a><a name="operator--"></a> checked_array_iterator:: operator--

Zmniejsza `checked_array_iterator` do poprzedniego elementu.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wartości, które są zwracane, `checked_array_iterator` a drugi, operator postdekrementacyjne, zwraca kopię, która zmniejszy `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator"></a><a name="op_add_eq"></a> checked_array_iterator:: operator + =

Dodaje określone przesunięcie do `checked_array_iterator` .

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, według którego ma zostać zwiększony iterator.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do którego odnosił się `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator"></a><a name="op_add"></a> checked_array_iterator:: operator +

Dodaje przesunięcie do iteratora i zwraca nowy odnoszący `checked_array_iterator` się do wstawionego elementu w nowym położeniu przesunięcia.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, które ma zostać dodane do `checked_array_iterator` .

### <a name="return-value"></a>Wartość zwracana

`checked_array_iterator`Adresowanie elementu przesunięcia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator-"></a><a name="operator-_eq"></a> checked_array_iterator:: operator-=

Zmniejsza określone przesunięcie od `checked_array_iterator` .

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, według którego ma zostać zwiększony iterator.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do którego odnosił się `checked_array_iterator` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratoroperator-"></a><a name="operator-"></a> checked_array_iterator:: operator-

Zmniejsza przesunięcie od iteratora i zwraca nowy odnoszący `checked_array_iterator` się do wstawionego elementu w nowym położeniu przesunięcia.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, które ma zostać zmniejszone od `checked_array_iterator` .

### <a name="return-value"></a>Wartość zwracana

`checked_array_iterator`Adresowanie elementu przesunięcia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_at"></a> checked_array_iterator:: operator []

Zwraca odwołanie do przesunięcia elementu z elementu, który jest adresowany przez `checked_array_iterator` określoną liczbę pozycji.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie od `checked_array_iterator` adresu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przesunięcia elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iteratorpointer"></a><a name="pointer"></a> checked_array_iterator::p ointer

Typ, który dostarcza wskaźnik do elementu, do którego odnosił się `checked_array_iterator` .

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator:: operator *](#op_star) , aby uzyskać przykład kodu.

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratorreference"></a><a name="reference"></a> checked_array_iterator:: Reference

Typ, który zawiera odwołanie do elementu, do którego odnosi się `checked_array_iterator` .

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład kodu, zobacz [checked_array_iterator:: operator []](#op_at) .

Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
