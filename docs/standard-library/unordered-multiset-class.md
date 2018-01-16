---
title: "unordered_multiset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_set/std::unordered_multiset
- unordered_set/std::unordered_multiset::allocator_type
- unordered_set/std::unordered_multiset::const_iterator
- unordered_set/std::unordered_multiset::const_local_iterator
- unordered_set/std::unordered_multiset::const_pointer
- unordered_set/std::unordered_multiset::const_reference
- unordered_set/std::unordered_multiset::difference_type
- unordered_set/std::unordered_multiset::hasher
- unordered_set/std::unordered_multiset::iterator
- unordered_set/std::unordered_multiset::key_equal
- unordered_set/std::unordered_multiset::key_type
- unordered_set/std::unordered_multiset::local_iterator
- unordered_set/std::unordered_multiset::pointer
- unordered_set/std::unordered_multiset::reference
- unordered_set/std::unordered_multiset::size_type
- unordered_set/std::unordered_multiset::value_type
- unordered_set/std::unordered_multiset::begin
- unordered_set/std::unordered_multiset::bucket
- unordered_set/std::unordered_multiset::bucket_count
- unordered_set/std::unordered_multiset::bucket_size
- unordered_set/std::unordered_multiset::cbegin
- unordered_set/std::unordered_multiset::cend
- unordered_set/std::unordered_multiset::clear
- unordered_set/std::unordered_multiset::count
- unordered_set/std::unordered_multiset::emplace
- unordered_set/std::unordered_multiset::emplace_hint
- unordered_set/std::unordered_multiset::empty
- unordered_set/std::unordered_multiset::end
- unordered_set/std::unordered_multiset::equal_range
- unordered_set/std::unordered_multiset::erase
- unordered_set/std::unordered_multiset::find
- unordered_set/std::unordered_multiset::get_allocator
- unordered_set/std::unordered_multiset::hash
- unordered_set/std::unordered_multiset::insert
- unordered_set/std::unordered_multiset::key_eq
- unordered_set/std::unordered_multiset::load_factor
- unordered_set/std::unordered_multiset::max_bucket_count
- unordered_set/std::unordered_multiset::max_load_factor
- unordered_set/std::unordered_multiset::max_size
- unordered_set/std::unordered_multiset::rehash
- unordered_set/std::unordered_multiset::size
- unordered_set/std::unordered_multiset::swap
- unordered_set/std::unordered_multiset::unordered_multiset
- unordered_set/std::unordered_multiset::operator=
- unordered_set/std::unordered_multiset::hash_function
dev_langs: C++
helpviewer_keywords:
- std::unordered_multiset
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
- std::unordered_multiset::unordered_multiset
- std::unordered_multiset::operator=
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash_function
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a958bf441809da24b317b777fd2f79946f3dc727
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unorderedmultiset-class"></a>unordered_multiset — Klasa
Klasa szablonu opisuje obiekt, który kontroluje sekwencji zróżnicowanych długość elementów typu `const Key`. Sekwencja jest słabo uporządkowana według funkcji mieszania, która dzieli sekwencję na uporządkowany zestaw podsekwencji, zwanych przedziałami, segmentami lub pakietami. W ramach każdego przedziału funkcja porównania określa, czy jakaś para elementów ma równoważną kolejność. Każdy element służy jako zarówno klucz sortowania, jak i wartość. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z wielu operacji, które mogą być niezależne od liczby elementów w sekwencji (stały czas), co najmniej kiedy wszystkie przedziały są w przybliżeniu jednakowej długości. W najgorszym przypadku, gdy wszystkie elementy znajdują się w jednym przedziale, liczba operacji jest proporcjonalna do liczby elementów w sekwencji (liniowy czas). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key>>  
class unordered_multiset;  
```  
  
#### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Key`|Typ klucza.|  
|`Hash`|Typ obiektu funkcji mieszania.|  
|`Pred`|Typ obiektu funkcji porównywania równości.|  
|`Alloc`|Klasa alokatora.|  
  
## <a name="members"></a>Elementy członkowskie  
  
|||  
|-|-|  
|Definicja typu|Opis|  
|[allocator_type](#allocator_type)|Typ alokatora do zarządzania pamięcią.|  
|[const_iterator](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[const_local_iterator](#const_local_iterator)|Typ iteratora stałego przedziału dla kontrolowanej sekwencji.|  
|[const_pointer](#const_pointer)|Typ stałego wskaźnika do elementu.|  
|[const_reference](#const_reference)|Typ stałego odwołania do elementu.|  
|[difference_type](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[hasher](#hasher)|Typ funkcji mieszania.|  
|[iteratora](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|  
|[key_equal](#key_equal)|Typ funkcji porównywania.|  
|[key_type](#key_type)|Typ klucza sortowania.|  
|[local_iterator](#local_iterator)|Typ iteratora przedziału dla kontrolowanej sekwencji.|  
|[wskaźnik](#pointer)|Typ wskaźnika do elementu.|  
|[Odwołanie](#reference)|Typ odwołania do elementu.|  
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|  
|[value_type](#value_type)|Typ elementu.|  
  
|||  
|-|-|  
|Funkcja elementów członkowskich|Opis|  
|[Rozpocznij](#begin)|Określa początek kontrolowanej sekwencji.|  
|[Zasobnik](#bucket)|Pobiera numer przedziału dla wartości klucza.|  
|[bucket_count](#bucket_count)|Pobiera liczbę przedziałów.|  
|[bucket_size](#bucket_size)|Pobiera rozmiar przedziału.|  
|[cbegin](#cbegin)|Określa początek kontrolowanej sekwencji.|  
|[cend](#cend)|Określa koniec kontrolowanej sekwencji.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy.|  
|[Liczba](#count)|Wyszukuje liczbę elementów pasujących do określonego klucza.|  
|[emplace](#emplace)|Dodaje element skonstruowany na miejscu.|  
|[emplace_hint](#emplace_hint)|Dodaje element skonstruowany na miejscu, z podpowiedzią.|  
|[pusty](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[koniec](#end)|Określa koniec kontrolowanej sekwencji.|  
|[equal_range](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[wymazywanie](#erase)|Usuwa elementy z określonych pozycji.|  
|[Znajdź](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[get_allocator](#get_allocator)|Pobiera przechowywany obiekt alokatora.|  
|[hash_function](#hash)|Pobiera przechowywany obiekt funkcji mieszania.|  
|[Wstaw](#insert)|Dodaje elementy.|  
|[key_eq](#key_eq)|Pobiera przechowywany obiekt funkcji porównywania.|  
|[load_factor —](#load_factor)|Oblicza średnią liczbę elementów na przedział.|  
|[max_bucket_count](#max_bucket_count)|Pobiera maksymalną liczbę przedziałów.|  
|[max_load_factor —](#max_load_factor)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[max_size](#max_size)|Pobiera maksymalny rozmiar kontrolowanej sekwencji.|  
|[rehash](#rehash)|Przebudowuje tabelę mieszania.|  
|[rozmiar](#size)|Liczy liczbę elementów.|  
|[swap](#swap)|Zamienia zawartości dwóch kontenerów.|  
|[unordered_multiset —](#unordered_multiset)|Konstruuje obiekt kontenera.|  
  
|||  
|-|-|  
|Operator|Opis|  
|[unordered_multiset::operator =](#op_eq)|Kopiuje tabelę mieszania.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt porządkuje sekwencji kontroluje wywołując dwa obiekty przechowywane obiektem porównanie funkcji typu [unordered_multiset::key_equal](#key_equal) i obiektu typu funkcji skrótu [unordered_multiset::hasher](#hasher). Dostęp do pierwszego obiektu przechowywanych przez wywołanie funkcji Członkowskich [unordered_multiset::key_eq](#key_eq)`()`; i dostępu do drugiego obiektu przechowywanych przez wywołanie funkcji Członkowskich [unordered_multiset::hash_ Funkcja](#hash)`()`. W szczególności dla wszystkich wartości `X` i `Y` typu `Key`, wywołanie `key_eq()(X, Y)` zwraca wartość true tylko wtedy, gdy wartości dwóch argumentów równoważne kolejności; wywołanie `hash_function()(keyval)` daje rozkład wartości typu `size_t`. W odróżnieniu od klasy szablonu [unordered_set — klasa](../standard-library/unordered-set-class.md), obiekt klasy szablonu `unordered_multiset` nie upewnij się, że `key_eq()(X, Y)` zawsze ma wartość false dla dowolnego dwa elementy kontrolowanej sekwencji. (Klucze nie muszą być unikatowy.)  
  
 Obiekt przechowuje również współczynnik maksymalnego obciążenia, który określa maksymalną żądaną średnią liczbę elementów na przedział. Jeśli Wstawianie elementu powoduje, że [unordered_multiset::load_factor](#load_factor) `()` przekroczyć współczynnika maksymalne obciążenie, zwiększa liczbę przedziałów, w kontenerze oraz odtwarza tablicy skrótów zgodnie z potrzebami.  
  
 Rzeczywista kolejność elementów w kontrolowanej sekwencji zależy od funkcji mieszania, funkcji porównywania, kolejności wstawiania, współczynnika maksymalnego obciążenia i bieżącej liczby przedziałów. Na ogół nie można przewidzieć kolejności elementów w kontrolowanej sekwencji. Można jednak zawsze mieć pewność, że dowolny podzbiór elementów, które mają równoważną kolejność, są obok siebie w kontrolowanej sekwencji.  
  
 Obiekt przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pośrednictwem typu obiektu alokatora przechowywanych [unordered_multiset::allocator_type](#allocator_type). Obiekt alokatora muszą mieć ten sam interfejs zewnętrznych jako obiekt klasy szablonu `allocator`. Należy zauważyć, że przechowywany obiekt alokatora nie jest kopiowany po przypisaniu obiektu kontenera.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<unordered_set >  
  
 **Namespace:** Standard  
  
##  <a name="allocator_type"></a>unordered_multiset::allocator_type  
 Typ alokatora do zarządzania pamięcią.  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Alloc`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="begin"></a>unordered_multiset::BEGIN  
 Określa początek kontrolowanej sekwencji lub zasobnika.  
  
```  
iterator begin();

const_iterator begin() const;

 
local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`nbucket`|Liczba zasobników.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji dwóch elementów członkowskich powrócić do przodu iteratora tego punktów w pierwszym elementem sekwencji (lub bezpośrednio po zakończeniu pustej sekwencji). Funkcje Członkowskie ostatnich dwóch powrócić do przodu iteratora tego punktów w pierwszym elemencie zasobnik `nbucket` (lub bezpośrednio po zakończeniu pusty zasobnik).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_begin.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect first two items " [c] [b]"   
    Myset::iterator it2 = c1.begin();   
    std::cout << " [" << *it2 << "]";   
    ++it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[c] [b]  
[a]  
```  
  
##  <a name="bucket"></a>unordered_multiset::Bucket  
 Pobiera numer przedziału dla wartości klucza.  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 keyval  
 Wartość klucza do mapowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę zasobników obecnie odpowiadającą wartości klucza `keyval`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="bucket_count"></a>unordered_multiset::bucket_count  
 Pobiera liczbę przedziałów.  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca bieżącą liczbę zasobników.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="bucket_size"></a>unordered_multiset::bucket_size  
 Pobiera rozmiar zasobnika  
  
```  
size_type bucket_size(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nbucket`  
 Liczba zasobników.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie zwraca rozmiar Liczba zasobników `nbucket`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="cbegin"></a>unordered_multiset::cbegin  
 Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dostępu do przodu, który wskazuje na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.  
  
 Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>unordered_multiset::cend  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dostępu do przodu, który wskazuje poza koniec zakresu.  
  
### <a name="remarks"></a>Uwagi  
 `cend`Służy do sprawdzenia, czy iteratora osiągnęła koniec zakresu.  
  
 Można użyć funkcji członkowskiej zamiast `end()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `end()` i `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
##  <a name="clear"></a>unordered_multiset::Clear  
 Usuwa wszystkie elementy.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [unordered_multiset::erase](#erase) `(` [unordered_multiset::begin](#begin) `(),` [unordered_multiset::end](#end) `())`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_clear.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="const_iterator"></a>unordered_multiset::const_iterator  
 Typ iteratora stałego dla kontrolowanej sekwencji.  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako stałej iteratora do przodu w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla zdefiniowanego typu `T1`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_local_iterator"></a>unordered_multiset::const_local_iterator  
 Typ iteratora stałego przedziału dla kontrolowanej sekwencji.  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako stałej iteratora do przodu zasobnika. Jest on opisany tutaj jako synonim dla zdefiniowanego typu `T5`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="const_pointer"></a>unordered_multiset::const_pointer  
 Typ stałego wskaźnika do elementu.  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako stałej wskaźnika do elementu w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_pointer p = &*it;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_reference"></a>unordered_multiset::const_reference  
 Typ stałego odwołania do elementu.  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako stałej odwołanie do elementu w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_reference ref = *it;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="count"></a>unordered_multiset::Count  
 Wyszukuje liczbę elementów pasujących do określonego klucza.  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów w zakresie rozdzielone [unordered_multiset::equal_range](#equal_range)`(keyval)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "count('A') == " << c1.count('A') << std::endl;   
    std::cout << "count('b') == " << c1.count('b') << std::endl;   
    std::cout << "count('C') == " << c1.count('C') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="difference_type"></a>unordered_multiset::difference_type  
 Typ odległości ze znakiem między dwoma elementami.  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wpisz liczbę całkowitą ze znakiem opisuje obiekt, który może reprezentować różnica między adresami dwóch elementów w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla zdefiniowanego typu `T3`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    std::cout << "end()-begin() == " << diff << std::endl;   
  
// compute negative difference   
    diff = 0;   
    for (Myset::const_iterator it = c1.end();   
        it != c1.begin(); --it)   
        --diff;   
    std::cout << "begin()-end() == " << diff << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="emplace"></a>unordered_multiset::emplace  
 Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane).  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do unordered_multiset.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas wstawiania Jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontenera nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynikiem jest niezdefiniowany.  
  
 Na przykład kod, zobacz [multiset::emplace](../standard-library/multiset-class.md#emplace).  
  
##  <a name="emplace_hint"></a>unordered_multiset::emplace_hint  
 Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane), ze wskazówką umieszczania.  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do unordered_multiset.|  
|`where`|Wskazówki dotyczące miejsca, aby rozpocząć wyszukiwanie poprawny punkt wstawiania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas wstawiania Jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, kontenera nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynikiem jest niezdefiniowany.  
  
 Na przykład kod, zobacz [set::emplace_hint](../standard-library/set-class.md#emplace_hint).  
  
##  <a name="empty"></a>unordered_multiset::Empty  
 Sprawdza, czy nie ma żadnych elementów.  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wartość true dla pustego kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_empty.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="end"></a>unordered_multiset::end  
 Określa koniec kontrolowanej sekwencji.  
  
```  
iterator end();
const_iterator end() const;

 
    local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nbucket`  
 Liczba zasobników.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji dwóch elementów członkowskich powrócić do przodu iteratora tego punktów bezpośrednio po zakończeniu sekwencji. Funkcje Członkowskie ostatnich dwóch powrócić do przodu iteratora tego punktów bezpośrednio po zakończeniu zasobnik `nbucket`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_end.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect last two items " [a] [b]"   
    Myset::iterator it2 = c1.end();   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));   
    --lit;   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a] [b]  
[a]  
```  
  
##  <a name="equal_range"></a>unordered_multiset::equal_range  
 Wyszukuje zakres, który odpowiada określonemu kluczowi.  
  
```  
std::pair<iterator, iterator>  
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>  
    equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca parę Iteratory `X` tak, aby `[X.first, X.second)` rozgranicza tylko te elementy kontrolowanej sekwencji mające porządkowanie równoważne z `keyval`. Jeśli nie istnieją żadne takie elementy, zarówno Iteratory są `end()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display results of failed search   
    std::pair<Myset::iterator, Myset::iterator> pair1 =   
        c1.equal_range('x');   
    std::cout << "equal_range('x'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
// display results of successful search   
    pair1 = c1.equal_range('b');   
    std::cout << "equal_range('b'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
equal_range('x'):  
equal_range('b'): [b]  
```  
  
##  <a name="erase"></a>unordered_multiset::ERASE  
 Usuwa element lub zakres elementów w unordered_multiset z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>Parametry  
 `Where`  
 Położenie elementu do usunięcia.  
  
 `First`  
 Pozycja pierwszego elementu do usunięcia.  
  
 `Last`  
 Pozycja poza ostatni element do usunięcia.  
  
 `Key`  
 Wartość klucza elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub element, który jest koniec unordered_multiset, jeśli nie zawiera żadnego takiego elementu.  
  
 Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z unordered_multiset.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład kod, zobacz [set::erase](../standard-library/set-class.md#erase).  
  
##  <a name="find"></a>unordered_multiset::Find  
 Wyszukuje element, który odpowiada określonemu kluczowi.  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [unordered_multiset::equal_range](#equal_range)`(keyval).first`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_find.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "find('A') == "   
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;   
  
// try to find and succeed   
    Myset::iterator it = c1.find('b');   
    std::cout << "find('b') == "   
        << std::boolalpha << (it != c1.end())   
        << ": [" << *it << "]" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
find('A') == false  
find('b') == true: [b]  
```  
  
##  <a name="get_allocator"></a>unordered_multiset::get_allocator  
 Pobiera przechowywany obiekt alokatora.  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca obiekt alokatora przechowywane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="hash"></a>unordered_multiset::hash_function  
 Pobiera przechowywany obiekt funkcji mieszania.  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca obiekt funkcji skrótu przechowywaną.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="hasher"></a>unordered_multiset::hasher  
 Typ funkcji mieszania.  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Hash`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_hasher.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="insert"></a>unordered_multiset::INSERT  
 Wstawia element lub zakres elementów do unordered_multiset.  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Val`|Wartość elementu ma zostać wstawiony do unordered_multiset.|  
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania.|  
|`ValTy`|Parametr szablonu, który określa typ argumentu, który unordered_multiset można używać do tworzenia elementu [value_type](../standard-library/map-class.md#value_type), a idealnych przekazuje `Val` jako argument.|  
|`First`|Pozycja pierwszego elementu do skopiowania.|  
|`Last`|Pozycja poza ostatni element do skopiowania.|  
|`InputIterator`|Argument funkcji szablonu, który spełnia wymagania [wejściowych iteratora](../standard-library/input-iterator-tag-struct.md) wskazującego elementów typu, który może służyć do utworzenia [value_type](../standard-library/map-class.md#value_type) obiektów.|  
|`IList`|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcje Członkowskie jednym elementu wstawienie (1) i (2) zwraca iteratora miejsce, w którym wstawiono nowy element do unordered_multiset.  
  
 Funkcje Członkowskie pojedynczego elementu z wskazówki, (3) i (4) zwraca iterację, który wskazuje miejsce, w którym wstawiono nowy element do unordered_multiset.  
  
### <a name="remarks"></a>Uwagi  
 Brak wskaźniki lub odwołania jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas wstawiania tylko jednego elementu jeśli wyjątek jest zgłaszany, ale nie występuje w funkcji skrótu kontenera, stan kontenera nie jest modyfikowany. Jeśli wyjątek jest zgłaszany w funkcji skrótu, wynikiem jest niezdefiniowany. Podczas wstawiania wiele elementów jeśli wyjątek kontenera pozostaje w stanie nieokreślony, ale prawidłowy.  
  
 [Value_type](../standard-library/map-class.md#value_type) kontenera jest element typedef, który należy do kontenera i zestawu `unordered_multiset<V>::value_type` jest typem `const V`.  
  
 Zakres funkcji członkowskiej [5] wstawia sekwencji wartości elementów do unordered_multiset odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja członkowska kontenera `end()` odwołuje się do położenia zaraz po ostatnim elementem w kontenerze — na przykład instrukcja `m.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `m`.  
  
 (6) używa funkcji członkowskiej liście inicjatorów [initializer_list](../standard-library/initializer-list.md) skopiuj elementy do unordered_multiset.  
  
 Do wstawienia elementu w miejscu skonstruować — to znaczy są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [unordered_multiset::emplace](#emplace) i [unordered_multiset::emplace_hint](#emplace_hint).  
  
 Na przykład kod, zobacz [multiset::insert](../standard-library/multiset-class.md#insert).  
  
##  <a name="iterator"></a>unordered_multiset::iterator  
 Typ, który zapewnia stałą [do przodu iteratora](../standard-library/forward-iterator-tag-struct.md) który może odczytywać elementów w unordered_multiset.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](../standard-library/multiset-class.md#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_eq"></a>unordered_multiset::key_eq  
 Pobiera przechowywany obiekt funkcji porównywania.  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca obiekt funkcja przechowywane porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_equal"></a>unordered_multiset::key_equal  
 Typ funkcji porównywania.  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Pred`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_type"></a>unordered_multiset::key_type  
 Typ klucza sortowania.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Key`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_key_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
##  <a name="load_factor"></a>unordered_multiset::load_factor  
 Oblicza średnią liczbę elementów na przedział.  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `(float)` [unordered_multiset::size](#size)`() / (float)`[unordered_multiset::bucket_count](#bucket_count)`()`, średnia liczba elementów na zasobnika.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="local_iterator"></a>unordered_multiset::local_iterator  
 Typ iteratora zasobnika.  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako do przodu iteratora zasobnika. Jest on opisany tutaj jako synonim dla zdefiniowanego typu `T4`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="max_bucket_count"></a>unordered_multiset::max_bucket_count  
 Pobiera maksymalną liczbę przedziałów.  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca maksymalną liczbę przedziałów, w obecnie dozwolone.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_load_factor"></a>unordered_multiset::max_load_factor  
 Pobiera lub ustawia maksymalną liczbę elementów na przedział.  
  
```  
float max_load_factor() const;

 
void max_load_factor(float factor);
```  
  
### <a name="parameters"></a>Parametry  
 `factor`  
 Nowy współczynnik maksymalne obciążenie.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element członkowski funkcja współczynnik przechowywanych maksymalne obciążenie. Drugi funkcji członkowskiej zastępuje współczynnik przechowywanych maksymalne obciążenie z `factor`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_size"></a>unordered_multiset::max_size  
 Pobiera maksymalny rozmiar kontrolowanej sekwencji.  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość najdłuższym sekwencji, który można kontrolować obiektem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_max_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 4294967295  
```  
  
##  <a name="op_eq"></a>unordered_multiset::operator =  
 Kopiuje tabelę mieszania.  
  
```  
unordered_multiset& operator=(const unordered_multiset& right);

unordered_multiset& operator=(unordered_multiset&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Unordered_multiset](../standard-library/unordered-multiset-class.md) kopiowane do `unordered_multiset`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `unordered_multiset`, `operator=` albo kopiuje lub przenosi zawartość `right` do `unordered_multiset`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// unordered_multiset_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_set>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_multiset<int> v1, v2, v3;  
   unordered_multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>unordered_multiset::Pointer  
 Typ wskaźnika do elementu.  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako wskaźnik do elementu w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::pointer p = &key;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="reference"></a>unordered_multiset::Reference  
 Typ odwołania do elementu.  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może służyć jako odwołanie do elementu w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::reference ref = key;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="rehash"></a>unordered_multiset::rehash  
 Przebudowuje tabelę mieszania.  
  
```  
void rehash(size_type nbuckets);
```  
  
### <a name="parameters"></a>Parametry  
 `nbuckets`  
 Żądaną liczbę zasobników.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zmienia Liczba zasobników, aby mieć co najmniej `nbuckets` i odtwarza tablicy skrótów zgodnie z potrzebami.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_rehash.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_load_factor() == 0.1  
```  
  
##  <a name="size"></a>unordered_multiset::size  
 Liczy liczbę elementów.  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="size_type"></a>unordered_multiset::size_type  
 Typ odległości bez znaku między dwoma elementami.  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typu Liczba całkowita bez znaku opisuje obiekt, który może reprezentować długość żadnych kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla zdefiniowanego typu `T2`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_size_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="swap"></a>unordered_multiset::swap  
 Zamienia zawartości dwóch kontenerów.  
  
```  
void swap(unordered_multiset& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Kontener wymiany.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia kontrolowanej sekwencji między `*this` i `right`. Jeśli [unordered_multiset::get_allocator](#get_allocator)`() == right.get_allocator()`robi to w czasie stałej, zgłasza wyjątek tylko w wyniku kopiowanie przechowywanych obiektów cech typu `Tr`, i jego unieważnienie żadnych odwołań, wskaźniki, lub Iteratory, które określają elementów w dwóch kontrolowanej sekwencji. W przeciwnym razie wykonuje szereg element zadania i wywołania konstruktora proporcjonalny do liczby elementów w dwóch kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_swap.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    Myset c2;   
  
    c2.insert('d');   
    c2.insert('e');   
    c2.insert('f');   
  
    c1.swap(c2);   
  
// display contents " [f] [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[f] [e] [d]  
[c] [b] [a]  
```  
  
##  <a name="unordered_multiset"></a>unordered_multiset::unordered_multiset  
 Konstruuje obiekt kontenera.  
  
```  
unordered_multiset(
    const unordered_multiset& Right);

explicit unordered_multiset(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());

unordered_multiset(
    unordered_multiset&& Right);

unordered_set(
    initializer_list<Type> IList);

unordered_set(
    initializer_list<Typ> IList,  
    size_type Bucket_count);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key,   
    const Allocator& Al);

template <class InputIterator>  
unordered_multiset(
 InputIterator First,   
    InputIterator Last,  
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`InputIterator`|Typ iteratora.|  
|`Al`|Obiekt alokatora, który ma być przechowywany.|  
|`Comp`|Obiekt funkcji porównywania, który ma być przechowywany.|  
|`Hash`|Obiekt funkcji mieszania, który ma być przechowywany.|  
|`Bucket_count`|Minimalna liczba przedziałów.|  
|`Right`|Kontener, który ma być skopiowany.|  
|`IList`|Initializer_list do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy konstruktora Określa kopię sekwencji kontrolowane przez `Right`. Drugi konstruktor określa pustą kontrolowaną sekwencję. Trzeci konstruktora wstawia sekwencja wartości elementu `[First, Last)`. Konstruktor czwarty określa kopiowania sekwencji przenosząc `Right`.  
  
 Wszystkie konstruktory również inicjują kilka przechowywanych wartości. Dla konstruktora kopiującego, wartości są uzyskiwane z `Right`. W przeciwnym razie:  
  
 Minimalna liczba zasobników jest argument `Bucket_count`, jeśli występuje; w przeciwnym razie jest wartość domyślna opisane tutaj jako wartość zdefiniowane w implementacji `N0`.  
  
 Obiekt funkcji skrótu jest argumentem `Hash`, jeśli występuje; w przeciwnym razie jest `Hash()`.  
  
 Obiekt funkcji porównania jest argumentem `Comp`, jeśli występuje; w przeciwnym razie jest `Comp()`.  
  
 Obiekt alokatora jest argument `Al`, jeśli występuje; w przeciwnym razie jest `Alloc()`.  
  
##  <a name="value_type"></a>unordered_multiset::value_type  
 Typ elementu.  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis elementu w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__unordered_set__unordered_multiset_value_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [< unordered_set >](../standard-library/unordered-set.md)   
 [Kontenery](../cpp/containers-modern-cpp.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

