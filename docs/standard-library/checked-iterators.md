---
title: Zaznaczone Iteratory | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SECURE_SCL_THROWS
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8997741b4290214aa8f147aa7b841424467e296b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="checked-iterators"></a>Zaznaczone iteratory
Iteratory sprawdzane zapewniają, że granice kontenera nie ulegają nadpisaniu. Zaznaczone Iteratory dotyczą zarówno kompilacje wydania i debugowanie kompilacji. Aby uzyskać więcej informacji o sposobie używania Iteratory debugowania podczas kompilowania w trybie debugowania, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).  
  
## <a name="remarks"></a>Uwagi  
Aby dowiedzieć się, jak wyłączyć ostrzeżenia, które są generowane przez zaznaczone Iteratory, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
Można użyć [ \_ITERATOR\_debugowania\_poziom](../standard-library/iterator-debug-level.md) makro preprocesora, aby włączyć lub wyłączyć funkcję zaznaczone Iteratory. Jeśli `_ITERATOR_DEBUG_LEVEL` jest zdefiniowany jako 1 lub 2, niebezpieczne użycie Iteratory powoduje błąd w czasie wykonywania i program zostanie zakończony. Jeśli jest zdefiniowana jako 0, iteratory sprawdzane są wyłączone. Domyślnie wartość `_ITERATOR_DEBUG_LEVEL` jest 0 dla wersji kompilacji i 2 dla kompilacje debugowania.  
  
> [!IMPORTANT]
> Starsze dokumentacji i kod źródłowy może odwoływać się do [_SECURE_SCL](../standard-library/secure-scl.md) makra. Użyj `_ITERATOR_DEBUG_LEVEL` do formantu `_SECURE_SCL`. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
Gdy `_ITERATOR_DEBUG_LEVEL` jest zdefiniowany jako 1 lub 2, te iteratora są sprawdzane:  
  
-   Wszystkie standardowe Iteratory (na przykład [vector::iterator](../standard-library/vector-class.md#iterator)) są sprawdzane.  
  
-   Iteratora dane wyjściowe w przypadku zaznaczenia iteratora, wywołania do biblioteki standardowej funkcji takich jak [std::copy](../standard-library/algorithm-functions.md#copy) zachowanie zaznaczenia.  
  
-   Iteratora dane wyjściowe w przypadku usunięcia zaznaczenia iteratora, wywołania funkcji biblioteki standardowej spowodować ostrzeżeń kompilatora.  
  
-   Następujące funkcje generować błąd wykonania w przypadku dostępu, który znajduje się poza granicami kontenera:  
  
|||||  
|-|-|-|-|  
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[Wstecz](../standard-library/deque-class.md#back)|[Front](../standard-library/deque-class.md#front)|  
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[Wstecz](../standard-library/list-class.md#back)|[Front](../standard-library/list-class.md#front)|[Wstecz](../standard-library/queue-class.md#back)|  
|[Front](../standard-library/queue-class.md#front)|[Vector::operator\[\]](../standard-library/vector-class.md#op_at)|[Wstecz](../standard-library/vector-class.md#back)|[Front](../standard-library/vector-class.md#front)|  
  
Gdy `_ITERATOR_DEBUG_LEVEL` jest zdefiniowana jako 0:  
  
-   Wszystkie standardowe Iteratory jest zaznaczony. Iteratory można przenieść poza granice kontenera, która prowadzi do niezdefiniowane zachowanie.  
  
-   Iteratora dane wyjściowe w przypadku zaznaczenia iteratora, wywołania do biblioteki standardowej funkcji takich jak `std::copy` zachowanie zaznaczenia.  
  
-   Iteratora dane wyjściowe w przypadku usunięcia zaznaczenia iteratora, wywołania funkcji biblioteki standardowej Pobierz zachowanie niezaznaczone.  
  
Checked iteratora odwołuje się do iteratora wywołującą `invalid_parameter_handler` Jeśli próbujesz przenieść poza granice tego kontenera. Aby uzyskać więcej informacji na temat `invalid_parameter_handler`, zobacz [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md).  
  
Adapterów iteratora, które obsługują zaznaczone Iteratory są [checked_array_iterator — klasa](../standard-library/checked-array-iterator-class.md) i [unchecked_array_iterator — klasa](../standard-library/unchecked-array-iterator-class.md).  
  
## <a name="example"></a>Przykład  
  
Podczas kompilowania przy użyciu `_ITERATOR_DEBUG_LEVEL` ustawiono wartość 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu, który znajduje się poza granicami kontenera za pomocą operatora indeksowania niektórych klas.  
  
```cpp  
// checked_iterators_1.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
   v.push_back(67);  
  
   int i = v[0];  
   cout << i << endl;  
  
   i = v[1]; //triggers invalid parameter handler  
}  
```  
  
Ten program drukuje "67", a następnie pojawia się okno dialogowe błędu potwierdzenia dodatkowe informacje o awarii.  
  
## <a name="example"></a>Przykład  
  
Podobnie podczas kompilowania przy użyciu `_ITERATOR_DEBUG_LEVEL` ustawiono wartość 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu za pomocą `front` lub `back` w klasach kontenera, gdy kontener jest pusta.  
  
```cpp  
// checked_iterators_2.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
  
   int& i = v.front(); // triggers invalid parameter handler  
}  
```  
  
Ten program pojawia się okno dialogowe błędu potwierdzenia dodatkowe informacje o awarii.  
  
## <a name="example"></a>Przykład  
  
Poniższy kod demonstruje różne scenariusze użycia iteratorów wraz z komentarzami dotyczącymi każdego z nich. Domyślnie `_ITERATOR_DEBUG_LEVEL` jest ustawiany 2 w kompilacjach debugowania i 0 w sprzedaży detalicznej kompilacji.  
  
```cpp  
// checked_iterators_3.cpp  
// cl.exe /MTd /EHsc /W4  
  
#include <algorithm>  
#include <array>  
#include <iostream>  
#include <iterator>  
#include <numeric>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename C> 
void print(const string& s, const C& c)  
{  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v(16);  
    iota(v.begin(), v.end(), 0);  
    print("v: ", v);  
  
    // OK: vector::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (an overrun causes a debug assertion)  
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (an overrun causes undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (an overrun causes a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode  
    // (it performs no checking, so an overrun causes undefined behavior)  
    int a8[16];  
    int * p8 = a8;  
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
  
```  
  
Podczas kompilowania tego kodu za pomocą `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` kompilator emituje ostrzeżenie, ale kompiluje bez błędów do pliku wykonywalnego:  
  
```Output  
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters 
that may be unsafe - this call relies on the caller to check that the passed values 
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation 
on how to use Visual C++ 'Checked Iterators'  
```  
  
Gdy są uruchomione w wierszu polecenia, pliku wykonywalnego, który generuje te dane wyjściowe:  
  
```Output  
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15  
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30  
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45  
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60  
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75  
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90  
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105  
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd biblioteki C++ Standard](../standard-library/cpp-standard-library-overview.md)   
 [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)

