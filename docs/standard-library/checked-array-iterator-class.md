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
ms.openlocfilehash: 688b93902da5b4492812b4715a248db9561ec258
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565717"
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator — Klasa

`checked_array_iterator` Klasa umożliwia przekształcenie tablicy lub wskaźnika w zaznaczony iterator. Ta klasa jest używana jako otoka (przy użyciu [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) funkcji) dla surowych wskaźników lub tablic jako ukierunkowany sposób zapewnienia sprawdzania i zarządzania ostrzeżeniami niezaznaczonych wskaźników zamiast globalnego wyciszania tych ostrzeżeń. Jeśli to konieczne, możesz użyć niezaznaczoną wersję tej klasy, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Ta klasa jest rozszerzeniem Microsoft standardowej biblioteki języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft. Aby uzyskać przykład pokazujący sposób pisania kodu, który nie wymaga użycia tej klasy, zobacz drugi przykład poniżej.

## <a name="syntax"></a>Składnia

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Uwagi

Ta klasa jest zdefiniowana w [stdext](../standard-library/stdext-namespace.md) przestrzeni nazw.

Aby uzyskać więcej informacji i przykładowy kod na temat funkcji sprawdzonego iteratora, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

Aby uniknąć konieczności `checked_array_iterator` klasy przy użyciu algorytmów standardowej biblioteki języka C++, rozważ użycie `vector` zamiast dynamicznie przydzielanej tablicy. Poniższy przykład demonstruje, jak to zrobić.

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
|[checked_array_iterator](#checked_array_iterator)|Tworzy domyślny `checked_array_iterator` lub `checked_array_iterator` z iteratora podstawowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma `checked_array_iterator`odwołującymi się do elementów w obrębie tego samego kontenera.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu odnoszącego `checked_array_iterator`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu odnoszącego `checked_array_iterator`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[base](#base)|Odzyskuje podstawowy iterator z jego `checked_array_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](#op_eq_eq)|Testuje dwa `checked_array_iterator`pod kątem równości.|
|[operator!=](#op_neq)|Testuje dwa `checked_array_iterator`pod kątem nierówności.|
|[Operator <](#op_lt)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy od `checked_array_iterator` po prawej stronie.|
|[operator>](#op_gt)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większy niż `checked_array_iterator` po prawej stronie.|
|[Operator < =](#op_lt_eq)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy niż lub równe `checked_array_iterator` po prawej stronie.|
|[operator>=](#op_gt_eq)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większy niż lub równa `checked_array_iterator` po prawej stronie.|
|[operator*](#op_star)|Zwraca element `checked_array_iterator` adresów.|
|[operator->](#op_arrow)|Zwraca wskaźnik do elementu kierowanego przez `checked_array_iterator`.|
|[operator++](#op_add_add)|Zwiększa `checked_array_iterator` do następnego elementu.|
|[operator--](#operator--)|Dekrementuje `checked_array_iterator` do poprzedniego elementu.|
|[operator+=](#op_add_eq)|Dodaje określone przesunięcie do `checked_array_iterator`.|
|[operator +](#op_add)|Dodaje wartość przesunięcia do iteratora i zwraca nowy `checked_array_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.|
|[operator-=](#operator-_eq)|Dekrementuje określone przesunięcie od `checked_array_iterator`.|
|[operator-](#operator-)|Dekrementuje przesunięcie od iteratora i zwraca nowy `checked_array_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do przesunięcia elementu z elementu kierowanego przez `checked_array_iterator` przez określoną liczbę pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** stdext

## <a name="base"></a>  checked_array_iterator::Base

Odzyskuje podstawowy iterator z jego `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator

Tworzy domyślny `checked_array_iterator` lub `checked_array _iterator` z iteratora podstawowego.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik do tablicy.

*Rozmiar*<br/>
Rozmiar tablicy.

*index*<br/>
(Opcjonalnie) Element w tablicy, aby zainicjować iteratora.  Domyślnie iterator który jest inicjowany do pierwszego elementu w tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="difference_type"></a>  checked_array_iterator::difference_type

Typ, który zawiera różnicę między dwoma `checked_array_iterator`odwołującymi się do elementów w obrębie tego samego kontenera.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`checked_array_iterator` Typu różnica jest taka sama jak typ różnicy iteratora.

Zobacz [checked_array_iterator::operator []](#op_at) przykładowy kod.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_eq_eq"></a>  checked_array_iterator::operator ==

Testuje dwa `checked_array_iterator`pod kątem równości.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Względem, który ma zostać sprawdzony pod kątem równości.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_neq"></a>  checked_array_iterator::operator! =

Testuje dwa `checked_array_iterator`pod kątem nierówności.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Względem, który ma zostać sprawdzony pod kątem nierówności.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_lt"></a>  checked_array_iterator::operator&lt;

Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy od `checked_array_iterator` po prawej stronie.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Względem, który ma zostać sprawdzony pod kątem nierówności.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_gt"></a>  checked_array_iterator::operator&gt;

Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większy niż `checked_array_iterator` po prawej stronie.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator&lt; ](#op_lt) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_lt_eq"></a>  checked_array_iterator::operator&lt;=

Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejszy niż lub równe `checked_array_iterator` po prawej stronie.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator&gt; = ](#op_gt_eq) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_gt_eq"></a>  checked_array_iterator::operator&gt;=

Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większy niż lub równa `checked_array_iterator` po prawej stronie.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
`checked_array_iterator` Ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_star"></a>  checked_array_iterator::operator *

Zwraca element `checked_array_iterator` adresów.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu kierowanego przez `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_arrow"></a>  checked_array_iterator::operator-&gt;

Zwraca wskaźnik do elementu kierowanego przez `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu kierowanego przez `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::pointer](#pointer) dla przykładu kodu.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_add_add"></a>  checked_array_iterator::operator ++

Zwiększa `checked_array_iterator` do następnego elementu.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca preincremented `checked_array_iterator` i drugi postinkrementacyjne operator zwraca kopię obiektu zwiększona `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="operator--"></a>  checked_array_iterator::operator--

Dekrementuje `checked_array_iterator` do poprzedniego elementu.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca predecremented `checked_array_iterator` i drugi postdekrementacyjne operator zwraca kopię obiektu wraz z przydzielaniem `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_add_eq"></a>  checked_array_iterator::operator +=

Dodaje określone przesunięcie do `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie, o którą należy zwiększyć iteratora.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu kierowanego przez `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="op_add"></a>  checked_array_iterator::operator +

Dodaje wartość przesunięcia do iteratora i zwraca nowy `checked_array_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie, które mają zostać dodane do `checked_array_iterator`.

### <a name="return-value"></a>Wartość zwracana

A `checked_array_iterator` odnoszący się do przesunięcia elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="operator-_eq"></a>  checked_array_iterator::operator-=

Dekrementuje określone przesunięcie od `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie, o którą należy zwiększyć iteratora.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu kierowanego przez `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="operator-"></a>  checked_array_iterator::operator-

Dekrementuje przesunięcie od iteratora i zwraca nowy `checked_array_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie do zmniejszenia z `checked_array_iterator`.

### <a name="return-value"></a>Wartość zwracana

A `checked_array_iterator` odnoszący się do przesunięcia elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_at"></a>  checked_array_iterator::operator]

Zwraca odwołanie do przesunięcia elementu z elementu kierowanego przez `checked_array_iterator` przez określoną liczbę pozycji.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie od `checked_array_iterator` adresu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przesunięcia elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

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

## <a name="pointer"></a>  checked_array_iterator::Pointer

Typ, który dostarcza wskaźnik do elementu odnoszącego `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator *](#op_star) przykładowy kod.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="reference"></a>  checked_array_iterator::Reference

Typ, który zawiera odwołanie do elementu odnoszącego `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Uwagi

Zobacz [checked_array_iterator::operator []](#op_at) przykładowy kod.

Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
