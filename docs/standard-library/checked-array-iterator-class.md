---
title: "checked_array_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8384c61f9a56f4196d940566cd2b18336bd4d853
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator — Klasa
`checked_array_iterator` Klasa umożliwia przekształcanie tablicy lub wskaźnika do zaznaczenia iteratora. Klasa jest używana jako otoka (przy użyciu [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) funkcji) dla wskaźników raw lub tablic jako docelowych sposób sprawdzania i zarządzanie ostrzeżenia wskaźnika niezaznaczone zamiast globalnie wykluczania tych ostrzeżeń. Jeśli to konieczne, można niezaznaczone wersja tej klasy, [unchecked_array_iterator —](../standard-library/unchecked-array-iterator-class.md).  
  
> [!NOTE]
>  Ta klasa jest rozszerzeniem Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft. Aby uzyskać przykład pokazujący sposób pisania kodu, który nie wymaga użycia tej klasy, zobacz drugi przykład poniżej.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class _Iterator>  
class checked_array_iterator;
```  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest zdefiniowana w [stdext —](../standard-library/stdext-namespace.md) przestrzeni nazw.  
  
 Aby uzyskać więcej informacji i przykładowy kod funkcję iteratora zaznaczone, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
( 0 1 2 3 4 )  
( 0 1 2 3 4 )  
*\  
```  
  
## <a name="example"></a>Przykład  
 Aby uniknąć konieczności `checked_array_iterator` klasy przy użyciu algorytmów standardowa biblioteka C++, rozważ użycie `vector` zamiast dynamicznie przydzielonego tablicy. Poniższy przykład demonstruje, jak to zrobić.  
  
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
\* Output:   
 0 1 2 3 4 5 6 7 8 9  
*\  
```  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[checked_array_iterator](#checked_array_iterator)|Tworzy domyślny `checked_array_iterator` lub `checked_array_iterator` z iteratora podstawowej.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwiema `checked_array_iterator`s odwołujących się do elementów w tym samym kontenerze.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu, który został opisany w `checked_array_iterator`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu, który został opisany w `checked_array_iterator`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[base](#base)|Odzyskuje podstawowej iteratora z jego `checked_array_iterator`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|Sprawdza dwie `checked_array_iterator`s pod kątem równości.|  
|[operator!=](#op_neq)|Sprawdza dwie `checked_array_iterator`s pod kątem nierówności.|  
|[Operator <](#op_lt)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejsza niż `checked_array_iterator` po prawej stronie.|  
|[operator>](#op_gt)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większa niż `checked_array_iterator` po prawej stronie.|  
|[Operator < =](#op_lt_eq)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejsze niż lub równe `checked_array_iterator` po prawej stronie.|  
|[operator>=](#op_gt_eq)|Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większa niż lub równa `checked_array_iterator` po prawej stronie.|  
|[operator *](#op_star)|Zwraca element, który `checked_array_iterator` adresów.|  
|[operator ->](#operator-_gt)|Zwraca wskaźnik do elementu dotyczy `checked_array_iterator`.|  
|[operator++](#op_add_add)|Zwiększa `checked_array_iterator` do następnego elementu.|  
|[operator--](#operator--)|Zmniejsza `checked_array_iterator` do poprzedniego elementu.|  
|[operator+=](#op_add_eq)|Dodaje określone przesunięcie do `checked_array_iterator`.|  
|[operator+](#op_add)|Dodaje przesunięcia do iteratora i zwraca nowy `checked_array_iterator` adresowania wstawiony element w nowe położenie przesunięcia.|  
|[operator-=](#operator-_eq)|Zmniejsza określone przesunięcie z `checked_array_iterator`.|  
|[operator-](#operator-)|Zmniejsza jako przesunięcia z iteratora i zwraca nowy `checked_array_iterator` adresowania wstawiony element w nowe położenie przesunięcia.|  
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do przesunięcia element z elementu dotyczy `checked_array_iterator` przez określoną liczbę pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** stdext —  
  
##  <a name="base"></a>  checked_array_iterator::Base  
 Odzyskuje podstawowej iteratora z jego `checked_array_iterator`.  
  
```
_Iterator base() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
The iterator underlying rpos is bpos & it points to: 1.  
*\  
```  
  
##  <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator  
 Tworzy domyślny `checked_array_iterator` lub `checked_array _iterator` z iteratora podstawowej.  
  
```
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do tablicy.  
  
 `size`  
 Rozmiar tablicy.  
  
 `index`  
 (Opcjonalnie) Element w tablicy, aby zainicjować iteratora.  Domyślnie iteratora zainicjowano pierwszy element w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
0 1 2 3 4   
0 1 2 3 4   
3  
*\  
```  
  
##  <a name="difference_type"></a>  checked_array_iterator::difference_type  
 Typ, który zawiera różnicę między dwiema `checked_array_iterator`s odwołujących się do elementów w tym samym kontenerze.  
  
```
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```  
  
### <a name="remarks"></a>Uwagi  
 `checked_array_iterator` Typu różnica jest taki sam jak typ różnica iteratora.  
  
 Zobacz [checked_array_iterator::operator []](#op_at) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="op_eq_eq"></a>  checked_array_iterator::operator ==  
 Sprawdza dwie `checked_array_iterator`s pod kątem równości.  
  
```
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Za pomocą którego chcesz sprawdzić pod kątem równości.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
checked_array_iterators are equal  
checked_array_iterators are not equal  
*\  
```  
  
##  <a name="op_neq"></a>  checked_array_iterator::operator! =  
 Sprawdza dwie `checked_array_iterator`s pod kątem nierówności.  
  
```
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Za pomocą którego chcesz wyszukać nierówności.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
checked_array_iterators are equal  
checked_array_iterators are not equal  
*\  
```  
  
##  <a name="op_lt"></a>  checked_array_iterator::operator&lt;  
 Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejsza niż `checked_array_iterator` po prawej stronie.  
  
```
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Za pomocą którego chcesz wyszukać nierówności.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
checked_output_iterator2 is not less than checked_output_iterator  
checked_output_iterator2 is less than checked_output_iterator  
*\  
```  
  
##  <a name="op_gt"></a>  checked_array_iterator::operator&gt;  
 Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większa niż `checked_array_iterator` po prawej stronie.  
  
```
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::operator&lt; ](#op_lt) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="lt_eq"></a>  checked_array_iterator::operator&lt;=  
 Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest mniejsze niż lub równe `checked_array_iterator` po prawej stronie.  
  
```
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::operator&gt; = ](#op_gt_eq) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="gt_eq"></a>  checked_array_iterator::operator&gt;=  
 Sprawdza, czy `checked_array_iterator` po lewej stronie operatora jest większa niż lub równa `checked_array_iterator` po prawej stronie.  
  
```
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `checked_array_iterator` Do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
checked_output_iterator2 is greater than or equal to checked_output_iterator  
checked_output_iterator2 is less than checked_output_iterator  
*\  
```  
  
##  <a name="op_star"></a>  checked_array_iterator::operator *  
 Zwraca element, który `checked_array_iterator` adresów.  
  
```
reference operator*() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu dotyczy `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
0  
1  
2  
3  
4  
b[0] = 0  
c[0].first = 10  
*\  
```  
  
##  <a name="checked_array_iterator__operator-_gt"></a>  checked_array_iterator::operator-&gt;  
 Zwraca wskaźnik do elementu dotyczy `checked_array_iterator`.  
  
```
pointer operator->() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu dotyczy `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::pointer](#pointer) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="op_add_add"></a>  checked_array_iterator::operator ++  
 Zwiększa `checked_array_iterator` do następnego elementu.  
  
```
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy operator zwraca preincremented `checked_array_iterator` , a drugie postincrement operator kopię zwiększany `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
6  
3  
77  
*\  
```  
  
##  <a name="checked_array_iterator__operator--"></a>  checked_array_iterator::operator--  
 Zmniejsza `checked_array_iterator` do poprzedniego elementu.  
  
```
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy operator zwraca predecremented `checked_array_iterator` , a drugie postdecrement operator kopię zmniejszany `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
6  
3  
6  
*\  
```  
  
##  <a name="op_add_eq"></a>  checked_array_iterator::operator +=  
 Dodaje określone przesunięcie do `checked_array_iterator`.  
  
```
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Przesunięcie, o którą należy zwiększyć iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu dotyczy `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
6  
199  
*\  
```  
  
##  <a name="op_add"></a>  checked_array_iterator::operator +  
 Dodaje przesunięcia do iteratora i zwraca nowy `checked_array_iterator` adresowania wstawiony element w nowe położenie przesunięcia.  
  
```
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Przesunięcia, które mają zostać dodane do `checked_array_iterator`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `checked_array_iterator` adresowania element przesunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
6  
199  
*\  
```  
  
##  <a name="checked_array_iterator__operator-_eq"></a>  checked_array_iterator::operator-=  
 Zmniejsza określone przesunięcie z `checked_array_iterator`.  
  
```
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Przesunięcie, o którą należy zwiększyć iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu dotyczy `checked_array_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
199  
3  
*\  
```  
  
##  <a name="checked_array_iterator__operator-"></a>  checked_array_iterator::operator-  
 Zmniejsza jako przesunięcia z iteratora i zwraca nowy `checked_array_iterator` adresowania wstawiony element w nowe położenie przesunięcia.  
  
```
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Przesunięcie do się wraz z przydzielaniem z `checked_array_iterator`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `checked_array_iterator` adresowania element przesunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::operator -](#operator-) dla przykładu kodu.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="op_at"></a>  checked_array_iterator::operator]  
 Zwraca odwołanie do przesunięcia element z elementu dotyczy `checked_array_iterator` przez określoną liczbę pozycji.  
  
```
reference operator[](difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Przesunięcie od `checked_array_iterator` adres.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu przesunięcie.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
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
\* Output:   
3  
*\  
```  
  
##  <a name="pointer"></a>  checked_array_iterator::Pointer  
 Typ, który dostarcza wskaźnik do elementu, który został opisany w `checked_array_iterator`.  
  
```
typedef typename iterator_traits<_Iterator>::pointer pointer;
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::operator *](#op_star) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
##  <a name="reference"></a>  checked_array_iterator::Reference  
 Typ, który zawiera odwołanie do elementu, który został opisany w `checked_array_iterator`.  
  
```
typedef typename iterator_traits<_Iterator>::reference reference;
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [checked_array_iterator::operator []](#op_at) przykładowy kod.  
  
 Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [\<iterator>](../standard-library/iterator.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



