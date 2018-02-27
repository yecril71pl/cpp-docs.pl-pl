---
title: "list — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
dev_langs:
- C++
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd49b0ce1ca80c1a006975df085c332f0ef99ad2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="list-class"></a>list — Klasa
Klasy list standardowa biblioteka C++ jest klasą szablonu sekwencji kontenerów, które utrzymują ich elementów w układzie liniowej i umożliwia efektywne wstawienia i usunięcia w dowolnym miejscu w sekwencji. Sekwencja jest przechowywany jako dwukierunkowy połączonej listy elementów, każda z nich zawiera członka typu *typu*.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <class Type, class Allocator= allocator<Type>>  
class list  
```  
  
#### <a name="parameters"></a>Parametry  
 *Typ*  
 Typ danych elementu mają być przechowywane w liście.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje o liście alokacji i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to **alokatora**\<*typu*>.  
  
## <a name="remarks"></a>Uwagi  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Wektory powinna być preferowanych kontenera zarządzania sekwencję, gdy jest dostępie do dowolnych i wstawiania lub usuwania elementów są tylko wymagane na końcu sekwencji. Działanie kontenera deque — klasa jest wyższego poziomu, gdy wymagany jest dostęp losowy i wstawienia i usunięcia na początku i na końcu sekwencji w warstwie premium.  
  
 Funkcje Członkowskie listy [scalania](#merge), [odwrotnej](#reverse), [unikatowy](#unique), [Usuń](#remove), i [remove_if](#remove_if) zostały zoptymalizowana pod kątem operacji na listę obiektów i oferty alternatywne wysokiej wydajności, aby ich odpowiedniki ogólnego.  
  
 Listy; Ponowna alokacja występuje, gdy funkcja członkowska musi Wstaw lub wymazać elementy listy. W takich przypadkach tylko Iteratory lub odwołania, które wskazują na wymazane części kontrolowanej sekwencji staną się nieprawidłowe.  
  
 Dołącz nagłówek standardowy standardowa biblioteka C++ \<listy > Aby zdefiniować [kontenera](../standard-library/stl-containers.md) szablonu listy klas i kilka szablonów pomocniczych.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[list](#list)|Tworzy listę o określonym rozmiarze lub elementów określonej wartości na lub z określonym `allocator` lub jako kopię niektóre inne listy.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla obiekt listy.|  
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element na liście.|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element na liście.|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane na liście do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element na liście.|  
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma Iteratory, które odwołują się do elementów w obrębie tej samej listy.|  
|[iterator](#iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element na liście.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do `const` element przechowywane na liście do odczytu i wykonywania `const` operacji.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu na liście odwróconej.|  
|[size_type](#size_type)|Typ, który oblicza liczbę elementów listy.|  
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywanych na liście.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przypisz](#assign)|Powoduje usunięcie elementów z listy, a następnie kopiuje nowy zbiór elementów na listę docelową.|  
|[back](#back)|Zwraca odwołanie do ostatniego elementu listy.|  
|[begin](#begin)|Zwraca iteratora adresowania pierwszy element na liście.|  
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszy element na liście.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy listy.|  
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszy element na liście odwróconej.|  
|[crend](#crend)|Zwraca iteratora const, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście odwróconej.|  
|[emplace](#emplace)|Wstawia element zbudowane w miejscu do listy na określonej pozycji.|  
|[emplace_back](#emplace_back)|Dodaje element skonstruowane w miejscu na końcu listy.|  
|[emplace_front](#emplace_front)|Dodaje element skonstruowane w miejscu na początku listy.|  
|[empty](#empty)|Testy, jeśli lista jest pusta.|  
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście.|  
|[wymazywanie](#erase)|Usuwa element lub zakres elementów na liście z określonych pozycji.|  
|[Front](#front)|Zwraca odwołanie do pierwszego elementu listy.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt używany do utworzenia listy.|  
|[insert](#insert)|Wstawia element lub liczba elementów lub zakres elementów do listy na określonej pozycji.|  
|[max_size](#max_size)|Zwraca maksymalną długość elementu listy.|  
|[merge](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy docelowej oraz zamówienia nowe, łączny zbiór elementów w kolejności rosnącej lub w określonej kolejności.|  
|[pop_back](#pop_back)|Usuwa element na końcu listy.|  
|[pop_front](#pop_front)|Usuwa element na początku listy.|  
|[push_back](#push_back)|Dodaje element na końcu listy.|  
|[push_front](#push_front)|Dodaje element na początku listy.|  
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszy element na liście odwróconej.|  
|[remove](#remove)|Usuwa elementy na liście spełniających określone wymagania.|  
|[remove_if](#remove_if)|Usuwa elementy na liście, dla których jest spełniony określony predykat.|  
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście odwróconej.|  
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar listy.|  
|[Reverse](#reverse)|Odwraca kolejność, w którym elementy występuje na liście.|  
|[Rozmiar](#size)|Zwraca liczbę elementów na liście.|  
|[sort](#sort)|Rozmieszcza elementy listy w kolejności rosnącej lub względem innych relacji kolejności.|  
|[splice](#splice)|Usuwa elementy z listy argumentów i wstawia je do listy docelowej.|  
|[swap](#swap)|Zamienia elementów listy.|  
|[unique](#unique)|Usuwa zduplikowane elementy sąsiednie lub sąsiadujących elementów, które spełniają niektóre binarne predykat z listy.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[list::operator=](#op_eq)|Zastępuje kopię innej listy elementów listy.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<listy >  
  
##  <a name="allocator_type"></a>  list::allocator_type  
 Typ, który reprezentuje klasę alokatora dla obiekt listy.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `allocator_type` synonim parametru szablonu jest **przydzielania.**  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator).  
  
##  <a name="assign"></a>  list::ASSIGN  
 Powoduje usunięcie elementów z listy, a następnie kopiuje nowy zbiór elementów na listę docelową.  
  
```  
void assign(
    size_type Count,  
    const Type& Val);

void assign  
    initializer_list<Type> IList);

template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania z listy argumentów.  
  
 `Last`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania z listy argumentów.  
  
 `Count`  
 Liczba kopii elementu wstawiane do listy.  
  
 `Val`  
 Wartość elementu wstawiane do listy.  
  
 `IList`  
 Initializer_list, który zawiera elementy do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy na liście, przypisz z oryginalnej listy lub pewne inne listy Wstawia określony zakres elementów na listę docelową albo wstawia kopie nowego elementu określonej wartości na listę docelową  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_assign.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    list<int> c1, c2;  
    list<int>::const_iterator cIter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    c1.assign(++c2.begin(), c2.end());  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    c1.assign(7, 4);  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    c1.assign({ 10, 20, 30, 40 });  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
}  
```  
  
```Output  
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40  
```  
  
##  <a name="back"></a>  list::back  
 Zwraca odwołanie do ostatniego elementu listy.  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ostatni element listy. Jeśli lista jest pusta, zwracana wartość jest niezdefiniowana.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **ponownie** jest przypisany do `const_reference`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana **ponownie** jest przypisany do **odwołania**, można zmodyfikować obiektu listy.  
  
 Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu na pustej liście.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_back.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.back( );  
   const int& ii = c1.front( );  
  
   cout << "The last integer of c1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The last integer of c1 is 11  
The next-to-last integer of c1 is 10  
```  
  
##  <a name="begin"></a>  list::BEGIN  
 Zwraca iteratora adresowania pierwszy element na liście.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, adresowania pierwszy element na liście lub do lokalizacji pomyślne pustej listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować elementów w obiekcie z listy. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iterator**, można zmodyfikować elementów w obiekcie z listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_begin.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
   list <int>::const_iterator c1_cIter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is " << *c1_Iter << endl;  
  
 *c1_Iter = 20;  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is now " << *c1_Iter << endl;  
  
   // The following line would be an error because iterator is const  
   // *c1_cIter = 200;  
}  
```  
  
```Output  
The first element of c1 is 1  
The first element of c1 is now 20  
```  
  
##  <a name="cbegin"></a>  list::cbegin  
 Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dwukierunkowego dostępu, wskazujące na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.  
  
 Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  list::cend  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dwukierunkowego dostępu, który wskazuje poza koniec zakresu.  
  
### <a name="remarks"></a>Uwagi  
 `cend` Służy do sprawdzenia, czy iteratora osiągnęła koniec zakresu.  
  
 Można użyć funkcji członkowskiej zamiast `end()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `end()` i `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
##  <a name="clear"></a>  list::Clear  
 Usuwa wszystkie elementy listy.  
  
```  
void clear();
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_clear.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "The size of the list is initially " << c1.size( ) << endl;  
   c1.clear( );  
   cout << "The size of list after clearing is " << c1.size( ) << endl;  
}  
```  
  
```Output  
The size of the list is initially 3  
The size of list after clearing is 0  
```  
  
##  <a name="const_iterator"></a>  list::const_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element na liście.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [ponownie](#back).  
  
##  <a name="const_pointer"></a>  list::const_pointer  
 Udostępnia wskaźnik do `const` element na liście.  
  
``` 
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie listy.  
  
##  <a name="const_reference"></a>  list::const_reference  
 Typ, który zawiera odwołanie do **const** element przechowywane na liście do odczytu i wykonywania **const** operacji.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reference` nie może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_const_ref.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const list <int> c2 = c1;  
   const int &i = c2.front( );  
   const int &j = c2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error because c2 is const  
   // c2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="const_reverse_iterator"></a>  list::const_reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element na liście.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po liście odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin).  
  
##  <a name="crbegin"></a>  list::crbegin  
 Zwraca const iteratora adresowania pierwszy element na liście odwróconej.  
  
```  
const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszy element na liście odwróconej (lub adresowania co była ostatnim elementem w stałe `list`).  
  
### <a name="remarks"></a>Uwagi  
 `crbegin` jest używany z listą odwróconej podobnie jak [list::begin](#begin) jest używany z `list`.  
  
 Z wartością zwracaną z `crbegin`, nie można zmodyfikować obiektu listy. [list::rbegin](#rbegin) może służyć do iterowania po listę wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_crbegin.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::const_reverse_iterator c1_crIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1_crIter = c1.crbegin( );  
   cout << "The last element in the list is " << *c1_crIter << "." << endl;  
}  
```  
  
```Output  
The last element in the list is 30.  
```  
  
##  <a name="crend"></a>  list::crend  
 Zwraca iteratora const, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście odwróconej.  
  
```  
const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [listy](../standard-library/list-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `list`).  
  
### <a name="remarks"></a>Uwagi  
 `crend` jest używany z listą odwróconej podobnie jak [list::end](#end) jest używany z `list`.  
  
 Z wartością zwracaną z `crend`, `list` obiektu nie może być modyfikowany.  
  
 `crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego `list`.  
  
 Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_crend.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::const_reverse_iterator c1_crIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_crIter = c1.crend( );  
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in   
                 // the list (to point to the first element here)  
   cout << "The first element in the list is: " << *c1_crIter << endl;  
}  
```  
  
```Output  
The first element in the list is: 10  
```  
  
##  <a name="difference_type"></a>  list::difference_type  
 Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów na liście w zakresie elementy wskazywana przez Iteratory.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakres elementów do , ale bez tego elementu wskazywanego przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez odwracalnego kontenerów, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez podany przez kontener dostępie swobodnym, takich jak Iteratory dostępie swobodnym [vector — klasa](../standard-library/vector-class.md).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <list>  
#include <algorithm>  
  
int main( )   
{  
   using namespace std;  
  
   list <int> c1;  
   list <int>::iterator   c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
    list <int>::difference_type df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="emplace"></a>  list::emplace  
 Wstawia element zbudowane w miejscu do listy na określonej pozycji.  
  
```  
void emplace(iterator Where, Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Where`|Pozycja w celu [listy](../standard-library/list-class.md) gdzie dodaje się pierwszym elementem.|  
|`val`|Element dodany na końcu `list`.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek `list` jest niezmieniony po lewej i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_emplace.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   list <string> c2;  
   string str("a");  
  
   c2.emplace(c2.begin(), move( str ) );  
   cout << "Moved first element: " << c2.back( ) << endl;  
}  
```  
  
```Output  
Moved first element: a  
```  
  
##  <a name="emplace_back"></a>  list::emplace_back  
 Dodaje element skonstruowane w miejscu na końcu listy.  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany na końcu [listy](../standard-library/list-class.md).|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek `list` jest niezmieniony po lewej i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_emplace_back.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   list <string> c2;  
   string str("a");  
  
   c2.emplace_back( move( str ) );  
   cout << "Moved first element: " << c2.back( ) << endl;  
}  
```  
  
```Output  
Moved first element: a  
```  
  
##  <a name="emplace_front"></a>  list::emplace_front  
 Dodaje element skonstruowane w miejscu na początku listy.  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany do początku [listy](../standard-library/list-class.md).|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek `list` jest niezmieniony po lewej i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_emplace_front.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   list <string> c2;  
   string str("a");  
  
   c2.emplace_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
Moved first element: a  
```  
  
##  <a name="empty"></a>  list::Empty  
 Testy, jeśli lista jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista jest pusta. **false** Jeśli lista nie jest pusta.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_empty.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   if ( c1.empty( ) )  
      cout << "The list is empty." << endl;  
   else  
      cout << "The list is not empty." << endl;  
}  
```  
  
```Output  
The list is not empty.  
```  
  
##  <a name="end"></a>  list::end  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście.  
  
```  
const_iterator end() const;
iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście. Jeśli lista jest pusta, następnie `list::end == list::begin`.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnęła koniec listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_end.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_Iter = c1.end( );  
   c1_Iter--;  
   cout << "The last integer of c1 is " << *c1_Iter << endl;  
  
   c1_Iter--;  
 *c1_Iter = 400;  
   cout << "The new next-to-last integer of c1 is "  
        << *c1_Iter << endl;  
  
   // If a const iterator had been declared instead with the line:  
   // list <int>::const_iterator c1_Iter;  
   // an error would have resulted when inserting the 400  
  
   cout << "The list is now:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
}  
```  
  
```Output  
The last integer of c1 is 30  
The new next-to-last integer of c1 is 400  
The list is now: 10 400 30  
```  
  
##  <a name="erase"></a>  list::ERASE  
 Usuwa element lub zakres elementów na liście z określonych pozycji.  
  
```  
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `Where`  
 Położenie elementu do usunięcia z listy.  
  
 `first`  
 Pozycja pierwszego elementu usunięty z listy.  
  
 `last`  
 Pozycja poza ostatni element usunięty z listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub wskaźnik na końcu listy, jeśli nie zawiera żadnego takiego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Nie; Ponowna alokacja występuje tak Iteratory i odwołań staną się nieprawidłowe tylko dla elementów wymazanej.  
  
 **ERASE** nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_erase.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 40 );  
   c1.push_back( 50 );  
   cout << "The initial list is:";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   c1.erase( c1.begin( ) );  
   cout << "After erasing the first element, the list becomes:";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
   Iter = c1.begin( );  
   Iter++;  
   c1.erase( Iter, c1.end( ) );  
   cout << "After erasing all elements but the first, the list becomes: ";  
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
}  
```  
  
```Output  
The initial list is: 10 20 30 40 50  
After erasing the first element, the list becomes: 20 30 40 50  
After erasing all elements but the first, the list becomes:  20  
```  
  
##  <a name="front"></a>  list::front  
 Zwraca odwołanie do pierwszego elementu listy.  
  
```  
reference front();
const_reference front() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest pusta, zwracany jest niezdefiniowana.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `front` jest przypisany do **odwołania**, można zmodyfikować obiektu listy.  
  
 Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu na pustej liście.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_front.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
  
   int& i = c1.front();  
   const int& ii = c1.front();  
  
   cout << "The first integer of c1 is " << i << endl;  
   i++;  
   cout << "The first integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The first integer of c1 is 10  
The first integer of c1 is 11  
```  
  
##  <a name="get_allocator"></a>  list::get_allocator  
 Zwraca kopię obiektu alokatora użyty do utworzenia listy.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez listę.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy listy Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_get_allocator.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects   
   // that use the default allocator.  
   list <int> c1;  
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );  
  
   // c3 will use the same allocator class as c1  
   list <int> c3( c1.get_allocator( ) );  
  
   list<int>::allocator_type xlst = c1.get_allocator( );  
   // You can now call functions on the allocator class used by c1  
}  
```  
  
##  <a name="insert"></a>  list::INSERT  
 Wstawia element lub liczba elementów lub zakres elementów do listy na określonej pozycji.  
  
```  
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>  
void insert(iterator Where, InputIterator First, InputIterator Last);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Where`|Pozycja na liście cel, gdzie dodaje się pierwszym elementem.|  
|`Val`|Wartość elementu wstawiane do listy.|  
|`Count`|Liczba elementów, które są umieszczone na liście.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów na liście argumentów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu spoza zakresu elementów na liście argumentów do skopiowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wstaw dwa pierwsze zwracają iteratora wskazującą położenie, w którym wstawiono nowy element do listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_class_insert.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    list <int> c1, c2;  
    list <int>::iterator Iter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    Iter = c1.begin();  
    Iter++;  
    c1.insert(Iter, 100);  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    Iter = c1.begin();  
    Iter++;  
    Iter++;  
    c1.insert(Iter, 2, 200);  
  
    cout << "c1 =";  
    for(auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    c1.insert(++c1.begin(), c2.begin(), --c2.end());  
  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    // initialize a list of strings by moving  
    list < string > c3;  
    string str("a");  
  
    c3.insert(c3.begin(), move(str));  
    cout << "Moved first element: " << c3.front() << endl;  
  
    // Assign with an initializer_list  
    list <int> c4{ {1, 2, 3, 4} };  
    c4.insert(c4.begin(), { 5, 6, 7, 8 });  
  
    cout << "c4 =";  
    for (auto c : c4)  
        cout << " " << c;  
    cout << endl;  
}  
```  
  
##  <a name="iterator"></a>  list::iterator  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element na liście.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **iterator** może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin).  
  
##  <a name="list"></a>  list::list  
 Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z określonego programu przydzielania lub kopii całości lub części niektóre inne listy.  
  
```  
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>  
list(InputIterator First, InputIterator Last);

template <class InputIterator>  
list(InputIterator First, InputIterator Last, const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa alokatora do wykorzystania z tym obiektem.|  
|`Count`|Liczba elementów na liście skonstruowany.|  
|`Val`|Wartość elementów na liście.|  
|`Right`|Lista skonstruowane listy ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Initializer_list, który zawiera elementy do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora ( `Al`) i zainicjuj listy.  
  
 [get_allocator](#get_allocator) zwraca kopię obiektu alokatora użyty do utworzenia listy.  
  
 Określ pierwsze dwa konstruktory początkowa lista jest pusta, drugi określenie typu alokatora ( `Al`) do użycia.  
  
 Trzeci konstruktora określa powtórzenia określonej liczby ( `Count`) elementów wartości domyślnej dla klasy **typu**.  
  
 Konstruktory czwartym i piątym Określ powtórzenia ( `Count`) elementy wartości `Val`.  
  
 Konstruktor szóstego Określa kopię listy `Right`.  
  
 Konstruktor siódmego przenosi listy `Right`.  
  
 Konstruktor ósmego użyto initializer_list do określenia elementów.  
  
 Następne dwa konstruktory skopiuj zakres `[First, Last)` listy.  
  
 Żaden z konstruktorów wykonania wszelkich przeniesień tymczasowe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_class_list.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    // Create an empty list c0  
    list <int> c0;  
  
    // Create a list c1 with 3 elements of default value 0  
    list <int> c1(3);  
  
    // Create a list c2 with 5 elements of value 2  
    list <int> c2(5, 2);  
  
    // Create a list c3 with 3 elements of value 1 and with the   
    // allocator of list c2  
    list <int> c3(3, 1, c2.get_allocator());  
  
    // Create a copy, list c4, of list c2  
    list <int> c4(c2);  
  
    // Create a list c5 by copying the range c4[ first,  last)  
    list <int>::iterator c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    list <int> c5(c4.begin(), c4_Iter);  
  
    // Create a list c6 by copying the range c4[ first,  last) and with   
    // the allocator of list c2  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    c4_Iter++;  
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());  
  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c2 =";  
    for (auto c : c2)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c3 =";  
    for (auto c : c3)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c4 =";  
    for (auto c : c4)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c5 =";  
    for (auto c : c5)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c6 =";  
    for (auto c : c6)  
        cout << " " << c;  
    cout << endl;  
  
    // Move list c6 to list c7  
    list <int> c7(move(c6));  
    cout << "c7 =";  
    for (auto c : c7)  
        cout << " " << c;  
    cout << endl;  
  
    // Construct with initializer_list  
    list<int> c8({ 1, 2, 3, 4 });  
    cout << "c8 =";  
    for (auto c : c8)  
        cout << " " << c;  
    cout << endl;  
}  
```  
  
```Output  
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4  
```  
  
##  <a name="max_size"></a>  list::max_size  
 Zwraca maksymalną długość elementu listy.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_max_size.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::size_type i;  
  
   i = c1.max_size( );  
   cout << "Maximum possible length of the list is " << i << "." << endl;  
}  
```  
  
##  <a name="merge"></a>  list::merge  
 Usuwa elementy z listy argumentów, wstawia je do listy docelowej oraz zamówienia nowe, łączny zbiór elementów w kolejności rosnącej lub w określonej kolejności.  
  
```  
void merge(list<Type, Allocator>& right);

template <class Traits>  
void merge(list<Type, Allocator>& right, Traits comp);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Lista argumentów do scalenia z listy docelowej.  
  
 `comp`  
 Operator porównania porządkowania elementów na liście.  
  
### <a name="remarks"></a>Uwagi  
 Lista argumentów `right` jest scalany z listy docelowej.  
  
 Zarówno argument, jak i docelowy musi być wyposażony w tej samej relacji porównania za pomocą którego wynikowa sekwencja jest może zostać określona. Domyślna kolejność dla pierwszej funkcji członkowskiej jest rosnącą. Drugi funkcji członkowskiej nakłada operacja porównania określona przez użytkownika `comp` klasy **cech**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_merge.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1, c2, c3;  
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;  
  
   c1.push_back( 3 );  
   c1.push_back( 6 );  
   c2.push_back( 2 );  
   c2.push_back( 4 );  
   c3.push_back( 5 );  
   c3.push_back( 1 );  
  
   cout << "c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   cout << "c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
  
   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order  
   c2.sort( greater<int>( ) );  
   cout << "After merging c1 with c2 and sorting with >: c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
  
   cout << "c3 =";  
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
      cout << " " << *c3_Iter;  
   cout << endl;  
  
   c2.merge( c3, greater<int>( ) );  
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
}  
```  
  
```Output  
c1 = 3 6  
c2 = 2 4  
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2  
c3 = 5 1  
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1  
```  
  
##  <a name="op_eq"></a>  list::operator =  
 Zastępuje kopię innej listy elementów listy.  
  
```  
list& operator=(const list& right);
list& operator=(list&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Listy](../standard-library/list-class.md) kopiowane do `list`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `list`, operator kopiuje lub przenosi zawartość `right` do `list`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_operator_as.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list<int> v1, v2, v3;  
   list<int>::iterator iter;  
  
   v1.push_back(10);  
   v1.push_back(20);  
   v1.push_back(30);  
   v1.push_back(40);  
   v1.push_back(50);  
  
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
   v2 = forward< list<int> >(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="pointer"></a>  list::Pointer  
 Udostępnia wskaźnik do elementu na liście.  
  
```
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie listy.  
  
##  <a name="pop_back"></a>  list::pop_back  
 Usuwa element na końcu listy.  
  
``` 
void pop_back();
```  
  
### <a name="remarks"></a>Uwagi  
 Ostatni element nie może być pusta. `pop_back` nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_pop_back.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The last element is: " << c1.back( ) << endl;  
  
   c1.pop_back( );  
   cout << "After deleting the element at the end of the list, "  
           "the last element is: " << c1.back( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The last element is: 2  
After deleting the element at the end of the list, the last element is: 1  
```  
  
##  <a name="pop_front"></a>  list::pop_front  
 Usuwa element na początku listy.  
  
``` 
void pop_front();
```  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element nie może być pusta. `pop_front` nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_pop_front.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The second element is: " << c1.back( ) << endl;  
  
   c1.pop_front( );  
   cout << "After deleting the element at the beginning of the list, "  
         "the first element is: " << c1.front( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The second element is: 2  
After deleting the element at the beginning of the list, the first element is: 2  
```  
  
##  <a name="push_back"></a>  list::push_back  
 Dodaje element na końcu listy.  
  
```  
void push_back(void push_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany na końcu listy.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek jest zgłaszany, lista pozostanie niezmieniony i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_push_back.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "Last element: " << c1.back( ) << endl;  
  
   c1.push_back( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New last element: " << c1.back( ) << endl;  
  
// move initialize a list of strings  
   list <string> c2;  
   string str("a");  
  
   c2.push_back( move( str ) );  
   cout << "Moved first element: " << c2.back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved first element: a  
```  
  
##  <a name="push_front"></a>  list::push_front  
 Dodaje element na początku listy.  
  
```  
void push_front(const Type& val);
void push_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element na początku listy.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek jest zgłaszany, lista pozostanie niezmieniony i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_push_front.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_front( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "First element: " << c1.front( ) << endl;  
  
   c1.push_front( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New first element: " << c1.front( ) << endl;  
  
// move initialize a list of strings  
   list <string> c2;  
   string str("a");  
  
   c2.push_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
First element: 1  
New first element: 2  
Moved first element: a  
```  
  
##  <a name="rbegin"></a>  list::rbegin  
 Zwraca iteratora, którego dotyczy pierwszy element na liście odwróconej.  
  
``` 
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwrotnej dwukierunkowego iteratora adresowania pierwszy element na liście odwróconej (lub adresowania co był ostatni element na liście stałe).  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z listą odwróconej podobnie jak [rozpocząć](#begin) jest używany z listy.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, można zmodyfikować obiektu listy.  
  
 `rbegin` może służyć do iterowania po listę wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_rbegin.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
   list <int>::reverse_iterator c1_rIter;  
  
   // If the following line replaced the line above, *c1_rIter = 40;  
   // (below) would be an error  
   //list <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1_rIter = c1.rbegin( );  
   cout << "The last element in the list is " << *c1_rIter << "." << endl;  
  
   cout << "The list is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an iteration through a list in   
   // reverse order  
   cout << "The reversed list is:";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << " " << *c1_rIter;  
   cout << endl;  
  
   c1_rIter = c1.rbegin( );  
 *c1_rIter = 40;  
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;  
}  
```  
  
```Output  
The last element in the list is 30.  
The list is: 10 20 30  
The reversed list is: 30 20 10  
The last element in the list is now 40.  
```  
  
##  <a name="reference"></a>  list::Reference  
 Typ, który zawiera odwołanie do elementu przechowywane na liście.  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_ref.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   int &i = c1.front( );  
   int &j = c1.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="remove"></a>  list::Remove  
 Usuwa elementy na liście spełniających określone wymagania.  
  
``` 
void remove(const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Wartość, która posiadanych przez element spowoduje usunięcie tego elementu z listy.  
  
### <a name="remarks"></a>Uwagi  
 Nie wpływa na kolejność elementów pozostałych.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_remove.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 5 );  
   c1.push_back( 100 );  
   c1.push_back( 5 );  
   c1.push_back( 200 );  
   c1.push_back( 5 );  
   c1.push_back( 300 );  
  
   cout << "The initial list is c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   list <int> c2 = c1;  
   c2.remove( 5 );  
   cout << "After removing elements with value 5, the list becomes c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The initial list is c1 = 5 100 5 200 5 300  
After removing elements with value 5, the list becomes c2 = 100 200 300  
```  
  
##  <a name="remove_if"></a>  list::remove_if  
 Usuwa elementy z listy, dla których jest spełniony określony predykat.  
  
``` 
template <class Predicate>  
void remove_if(Predicate pred)  
```  
  
### <a name="parameters"></a>Parametry  
 `pred`  
 Predykat jednoargumentowe, które, jeśli spełnione przez element, powoduje usunięcie elementu z listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_remove_if.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
template <class T> class is_odd : public std::unary_function<T, bool>   
{  
public:  
   bool operator( ) ( T& val )   
   {  
   return ( val % 2 ) == 1;  
   }  
};  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 3 );  
   c1.push_back( 4 );  
   c1.push_back( 5 );  
   c1.push_back( 6 );  
   c1.push_back( 7 );  
   c1.push_back( 8 );  
  
   cout << "The initial list is c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   list <int> c2 = c1;  
   c2.remove_if( is_odd<int>( ) );  
  
   cout << "After removing the odd elements, "  
        << "the list becomes c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The initial list is c1 = 3 4 5 6 7 8  
After removing the odd elements, the list becomes c2 = 4 6 8  
```  
  
##  <a name="rend"></a>  list::rend  
 Zwraca iteratora, którego dotyczy lokalizacji, w której następuje ostatnim elementem na liście odwróconej.  
  
``` 
const_reverse_iterator rend() const;
reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście odwróconej (lokalizacja miał przed pierwszym elementem na liście stałe).  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z listą odwróconej podobnie jak [zakończenia](#end) jest używany z listy.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu listy. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, można zmodyfikować obiektu listy.  
  
 `rend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec listy.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_rend.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
   list <int>::reverse_iterator c1_rIter;  
  
   // If the following line had replaced the line above, an error would   
   // have resulted in the line modifying an element (commented below)  
   // because the iterator would have been const  
   // list <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rend( );  
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in   
                 // the list (to point to the first element here)  
   cout << "The first element in the list is: " << *c1_rIter << endl;  
  
   cout << "The list is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   // rend can be used to test if an iteration is through all of the   
   // elements of a reversed list  
   cout << "The reversed list is:";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << " " << *c1_rIter;  
   cout << endl;  
  
   c1_rIter = c1.rend( );  
   c1_rIter--;  // Decrementing the reverse iterator moves it backward   
                // in the reversed list (to the last element here)  
  
 *c1_rIter = 40;  // This modification of the last element would have   
                    // caused an error if a const_reverse iterator had   
                    // been declared (as noted above)  
  
   cout << "The modified reversed list is:";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << " " << *c1_rIter;  
   cout << endl;  
}  
```  
  
```Output  
The first element in the list is: 10  
The list is: 10 20 30  
The reversed list is: 30 20 10  
The modified reversed list is: 30 20 40  
```  
  
##  <a name="resize"></a>  list::Resize  
 Określa nowy rozmiar listy.  
  
``` 
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newsize`  
 Nowy rozmiar listy.  
  
 `val`  
 Wartość nowych elementów do dodania do listy nowy rozmiar jest większy który oryginalny rozmiar. W przypadku pominięcia wartości nowe elementy są przypisane wartości domyślne dla klasy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli rozmiar listy jest mniejszy niż rozmiar żądanej `_Newsize`, elementy są dodawane do listy, dopóki nie osiągnie żądanego rozmiaru.  
  
 Jeśli rozmiar listy jest większy niż rozmiar żądanej, najbliżej końca listy elementów są usuwane, dopóki nie osiągnie rozmiar listy `_Newsize`.  
  
 Jeśli występuje rozmiar listy jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.  
  
 [rozmiar](#size) odzwierciedla bieżący rozmiar listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_resize.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{   
   using namespace std;  
   list <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1.resize( 4,40 );  
   cout << "The size of c1 is " << c1.size( ) << endl;  
   cout << "The value of the last element is " << c1.back( ) << endl;  
  
   c1.resize( 5 );  
   cout << "The size of c1 is now " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
  
   c1.resize( 2 );  
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
}  
```  
  
```Output  
The size of c1 is 4  
The value of the last element is 40  
The size of c1 is now 5  
The value of the last element is now 0  
The reduced size of c1 is: 2  
The value of the last element is now 20  
```  
  
##  <a name="reverse"></a>  list::reverse  
 Odwraca kolejność, w którym elementy występuje na liście.  
  
``` 
void reverse();
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_reverse.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.reverse( );  
   cout << "Reversed c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
c1 = 10 20 30  
Reversed c1 = 30 20 10  
```  
  
##  <a name="reverse_iterator"></a>  list::reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu na liście odwróconej.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` jest używany do iterowania po liście odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin).  
  
##  <a name="size"></a>  list::size  
 Zwraca liczbę elementów na liście.  
  
``` 
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_size.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list <int> c1;  
   list <int>::size_type i;  
  
   c1.push_back( 5 );  
   i = c1.size( );  
   cout << "List length is " << i << "." << endl;  
  
   c1.push_back( 7 );  
   i = c1.size( );  
   cout << "List length is now " << i << "." << endl;  
}  
```  
  
```Output  
List length is 1.  
List length is now 2.  
```  
  
##  <a name="size_type"></a>  list::size_type  
 Typ, który oblicza liczbę elementów listy.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size).  
  
##  <a name="sort"></a>  list::sort  
 Rozmieszcza elementy listy w kolejności rosnącej lub względem niektóre określone przez użytkownika kolejności.  
  
``` 
void sort();

template <class Traits>  
void sort(Traits comp);
```  
  
### <a name="parameters"></a>Parametry  
 `comp`  
 Operator porównania porządkowania kolejnych elementów.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej umieszcza elementy w kolejności rosnącej domyślnie.  
  
 Funkcja szablonu elementu członkowskiego Porządkuje elementy zgodnie z operacja porównania określona przez użytkownika `comp` klasy **cech**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_sort.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter;  
  
   c1.push_back( 20 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
  
   cout << "Before sorting: c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.sort( );  
   cout << "After sorting c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.sort( greater<int>( ) );  
   cout << "After sorting with 'greater than' operation, c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
Before sorting: c1 = 20 10 30  
After sorting c1 = 10 20 30  
After sorting with 'greater than' operation, c1 = 30 20 10  
```  
  
##  <a name="splice"></a>  list::splice  
 Usuwa elementy z listy źródeł i wstawia je do listy docelowej.  
  
```  
// insert the entire source list  
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source); 

// insert one element of the source list  
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);
 
// insert a range of elements from the source list  
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```  
  
### <a name="parameters"></a>Parametry  
 `Where`  
 Pozycja na liście docelowej przed do wstawienia.  
  
 `Source`  
 Lista źródeł, który ma zostać umieszczone na liście docelowej.  
  
 `Iter`  
 Element, który ma zostać wstawiony z listy źródeł.  
  
 `First`  
 Pierwszym elementem w zakresie ma zostać wstawiony z listy źródeł.  
  
 `Last`  
 Pierwszą pozycję po ostatnim elemencie zakresu, który ma zostać wstawiony z listy źródeł.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy pary funkcji Członkowskich wstawia wszystkie elementy z listy źródeł do listy docelowej przed pozycji odwołuje się `Where` i usuwa wszystkie elementy z listy źródeł. ( `&Source` nie może być równa `this`.)  
  
 Druga para funkcji Członkowskich wstawia odwołuje się element `Iter` przed pozycji na liście docelowej, określone przez `Where` i usuwa `Iter` z listy źródeł. (Jeśli `Where == Iter || Where == ++Iter`, Brak zmian.)  
  
 Trzeci pary funkcji Członkowskich Wstawia zakres wskazywany przez [ `First`, `Last`) przed elementu na liście docelowej, określone przez `Where` i usuwa ten zakres elementów z listy źródeł. (Jeśli `&Source == this`, zakres `[First, Last)` nie może zawierać elementu wskazywanego przez `Where`.)  
  
 Jeśli wstawia łączenia ranged `N` elementów, i `&Source != this`, obiekt klasy [iterator](../standard-library/forward-list-class.md#iterator) jest zwiększany `N` razy.  
  
 We wszystkich przypadkach Iteratory, wskaźniki lub odwołania, które odwołują się do połączonego elementy ważność i nie są przenoszone do kontenera docelowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_splice.cpp  
// compile with: /EHsc /W4  
#include <list>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: ";  
  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    list<int> c1{10,11};  
    list<int> c2{20,21,22};  
    list<int> c3{30,31};  
    list<int> c4{40,41,42,43};  
  
    list<int>::iterator where_iter;  
    list<int>::iterator first_iter;  
    list<int>::iterator last_iter;  
  
    cout << "Beginning state of lists:" << endl;  
    cout << "c1 = ";  
    print(c1);  
    cout << "c2 = ";  
    print(c2);  
    cout << "c3 = ";  
    print(c3);  
    cout << "c4 = ";  
    print(c4);  
  
    where_iter = c2.begin();  
    ++where_iter; // start at second element  
    c2.splice(where_iter, c1);  
    cout << "After splicing c1 into c2:" << endl;  
    cout << "c1 = ";  
    print(c1);  
    cout << "c2 = ";  
    print(c2);  
  
    first_iter = c3.begin();  
    c2.splice(where_iter, c3, first_iter);  
    cout << "After splicing the first element of c3 into c2:" << endl;  
    cout << "c3 = ";  
    print(c3);  
    cout << "c2 = ";  
    print(c2);  
  
    first_iter = c4.begin();  
    last_iter = c4.end();  
    // set up to get the middle elements  
    ++first_iter;  
    --last_iter;  
    c2.splice(where_iter, c4, first_iter, last_iter);  
    cout << "After splicing a range of c4 into c2:" << endl;  
    cout << "c4 = ";  
    print(c4);  
    cout << "c2 = ";  
    print(c2);  
}  
  
```  
  
```Output  
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)  
```  
  
##  <a name="swap"></a>  list::swap  
 Zamienia elementów listy.  
  
``` 
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)  
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Lista zawierająca elementy zamianę lub listę, której elementy są wymienianych z tymi listy `left`.  
  
 `left`  
 Listę, której elementy są wymienianych z tymi listy `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_swap.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list <int> c1, c2, c3;  
   list <int>::iterator c1_Iter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 3 );  
   c2.push_back( 10 );  
   c2.push_back( 20 );  
   c3.push_back( 100 );  
  
   cout << "The original list c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.swap( c2 );  
  
   cout << "After swapping with c2, list c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap( c1,c3 );  
  
   cout << "After swapping with c3, list c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original list c1 is: 1 2 3  
After swapping with c2, list c1 is: 10 20  
After swapping with c3, list c1 is: 100  
```  
  
##  <a name="unique"></a>  list::UNIQUE  
 Usuwa zduplikowane elementy sąsiednie lub sąsiadujących elementów, które spełniają niektóre binarne predykat z listy.  
  
```  
void unique();

template <class BinaryPredicate>  
void unique(BinaryPredicate pred);
```  
  
### <a name="parameters"></a>Parametry  
 `pred`  
 Predykat binarne użyty do porównania kolejnych elementów.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja przyjęto założenie, że lista jest posortowana, tak, aby wszystkie zduplikowane elementy znajdują się obok siebie. Duplikaty, które nie są sąsiadujące nie zostaną usunięte.  
  
 Pierwszy funkcji członkowskiej Usuwa każdy element, który porównuje równa jej poprzedniego elementu.  
  
 Drugi funkcji członkowskiej Usuwa każdy element, który spełnia funkcji predykatu `pred` w porównaniu z jej poprzedniego elementu. Można użyć dowolnego z obiektów binarnych funkcja zadeklarowana w `<functional>`nagłówek argument pred lub utworzyć własne.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_unique.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   list <int> c1;  
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;  
   not_equal_to<int> mypred;  
  
   c1.push_back( -10 );  
   c1.push_back( 10 );  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 20 );  
   c1.push_back( -10 );  
  
   cout << "The initial list is c1 =";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   list <int> c2 = c1;  
   c2.unique( );  
   cout << "After removing successive duplicate elements, c2 =";  
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
      cout << " " << *c2_Iter;  
   cout << endl;  
  
   list <int> c3 = c2;  
   c3.unique( mypred );  
   cout << "After removing successive unequal elements, c3 =";  
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
      cout << " " << *c3_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The initial list is c1 = -10 10 10 20 20 -10  
After removing successive duplicate elements, c2 = -10 10 20 -10  
After removing successive unequal elements, c3 = -10 -10  
```  
  
##  <a name="value_type"></a>  list::value_type  
 Typ, który reprezentuje typ danych przechowywanych na liście.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `value_type` synonim parametru szablonu jest **typu**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_value_type.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   list<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<list>](../standard-library/list.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

