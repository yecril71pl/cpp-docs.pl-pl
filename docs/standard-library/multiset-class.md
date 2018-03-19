---
title: "multiset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8953fd24b62784e36f12fb96e3005e21a86bc62
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="multiset-class"></a>multiset — Klasa
Standardowa biblioteka C++ multiset — klasa jest używana do przechowywania i pobierania danych z kolekcji, w której wartości elementów zawartych nie musi być unikatowa i które służą jako wartości klucza, zgodnie z którymi automatycznie porządkowania danych. Nie można bezpośrednio zmienić wartości klucza elementu w zestawie wielokrotnym. Zamiast tego trzeba usunąć stare wartości i wstawić elementy z nowymi wartościami.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>  
class multiset  
```  
  
#### <a name="parameters"></a>Parametry  
 *Key*  
 Typ danych elementu do przechowywania w zestawie wielokrotnym.  
  
 *Porównaj*  
 Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w zestawie wielokrotnym. Predykat binarne **mniej**\<klucza > jest to wartość domyślna.  
  
 W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji zestawu wielokrotnego i dezalokacji pamięci. Wartość domyślna to **alokatora ***\<klucza >.*  
  
## <a name="remarks"></a>Uwagi  
 Standardowa biblioteka C++ multiset — klasa jest:  
  
-   Kontener asocjacyjny, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.  
  
-   Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.  
  
-   Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.  
  
-   Wielokrotny w tym sensie, że jego elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów z nią skojarzonych.  
  
-   Prosty kontener asocjacyjny, ponieważ jego wartości elementu są jego wartościami klucza.  
  
-   Klasa szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy. Typ danych, który ma być użyty, jest zamiast tego określony jako parametr w klasie szablonu wraz z funkcją porównania i alokatorem.  
  
 Iterator dostarczonych przez multiset — klasa jest iteratora dwukierunkowego, ale funkcji elementów członkowskich klasy [Wstaw](#insert) i [multiset](#multiset) wersje przyjmować jako parametry szablonu słabszych iteratora wejściowych, wymagania funkcji, których są bardziej minimalne niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory [ `First`, `Last`) w kontekście funkcji członkowskich tej klasy.  
  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.  
  
 Zestaw wielokrotny powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementów zestawu wielokrotnego może być wiele, mogą służyć jako własne klucze sortowania, więc klucze nie są unikatowe. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Gdyby nie zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera byłby zestaw. Gdyby unikatowe definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, mapa byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast definicje nie były unikatowe, mapa wielokrotna byłaby kontenerem z wyboru.  
  
 Zestaw wielokrotny porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu przechowywanej funkcji `Compare`. Ten obiekt przechowywanych jest funkcja porównanie, które mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argument *x* i *y* i wartością zwracaną **true** lub **false**. Kolejność na zestaw jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty x i y są zdefiniowane jako równoważne, gdy oba *f*( *x, y*) i *f*( *y, x*) to wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.  
  
 W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[Zestaw wielokrotny](#multiset)|Konstruuje `multiset` jest pusta lub będący kopię wszystkich lub określonej części `multiset`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Element typedef dla `allocator` klasy dla `multiset` obiektu.|  
|[const_iterator](#const_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytywać `const` element `multiset`.|  
|[const_pointer](#const_pointer)|Element typedef dla wskaźnika do `const` element `multiset`.|  
|[const_reference](#const_reference)|Element TypeDef stanowi odwołanie do `const` element przechowywane w `multiset` do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który można odczytać `const` element `multiset`.|  
|[difference_type](#difference_type)|Typem typedef całkowita liczba elementów `multiset` w zakresie między elementami wskazywana przez Iteratory.|  
|[iterator](#iterator)|Element typedef dla iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w `multiset`.|  
|[key_compare](#key_compare)|Element typedef dla obiekt funkcji, który można porównać dwa klucze, aby określić względną kolejność dwóch elementów w `multiset`.|  
|[key_type](#key_type)|Element typedef dla obiekt funkcji, który można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset`.|  
|[pointer](#pointer)|Element typedef dla wskaźnika do elementu `multiset`.|  
|[Odwołanie](#reference)|Typedef dla odwołania do elementu przechowywane w `multiset`.|  
|[reverse_iterator](#reverse_iterator)|Element typedef dla iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `multiset`.|  
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `multiset`.|  
|[value_compare —](#value_compare)|Element typedef dla obiekt funkcji, który można porównać dwóch elementów jako klucze sortowania, aby określić ich kolejność względne w `multiset`.|  
|[value_type](#value_type)|Element typedef, który opisuje obiekt zapisany jako elementu jako `multiset` jako wartość.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[begin](#begin)|Zwraca iteratora wskazujące pierwszy element w `multiset`.|  
|[cbegin](#cbegin)|Zwraca iteratora const, którego dotyczy pierwszym elementem w `multiset`.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `multiset`.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy `multiset`.|  
|[Liczba](#count)|Zwraca liczbę elementów w `multiset` którego klucz jest zgodny z kluczem określonym jako parametr.|  
|[crbegin](#crbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.|  
|[crend](#crend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|  
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `multiset`.|  
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `multiset`, ze wskazówką umieszczania.|  
|[empty](#empty)|Sprawdza, czy `multiset` jest pusta.|  
|[Koniec](#end)|Zwraca iterację wskazuje lokalizację za ostatnim elementem w `multiset`.|  
|[equal_range](#equal_range)|Zwraca parę iteratorów. Pierwszy iteratora w punktach pary do pierwszego elementu w `multiset` za pomocą klucza, który jest większy niż określony klucz. Drugi iteratora w punktach pary do pierwszego elementu w `multiset` za pomocą klucza jest równa lub większa niż klucz.|  
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `multiset` z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.|  
|[Znajdź](#find)|Zwraca iterację wskazuje lokalizację pierwszego elementu w `multiset` mający klucza równą określonego klucza.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt, który jest używany do tworzenia `multiset`.|  
|[insert](#insert)|Wstawia element lub zakres elementów do `multiset`.|  
|[key_comp](#key_comp)|Udostępnia obiekt funkcji, który można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multiset`.|  
|[lower_bound](#lower_bound)|Zwraca pierwszy element w iteratora `multiset` za pomocą klucza, który jest równy lub większy niż określony klucz.|  
|[max_size](#max_size)|Zwraca maksymalną długość `multiset`.|  
|[rbegin](#rbegin)|Zwraca iteratora wskazujące pierwszy element w odwróconej `multiset`.|  
|[rend](#rend)|Zwraca wartość wskazującą lokalizację pomyślne ostatnim elementem w odwróconej iteratora `multiset`.|  
|[Rozmiar](#size)|Zwraca liczbę elementów w `multiset`.|  
|[swap](#swap)|Zamienia elementy dwóch `multiset`s.|  
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `multiset` za pomocą klucza, który jest większy niż określony klucz.|  
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, który jest używany do wartości elementu kolejności w `multiset`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Zastępuje elementy `multiset` z kopią innego `multiset`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawić >  
  
 **Namespace:** Standard  
  
##  <a name="allocator_type"></a>  multiset::allocator_type  
 Reprezentuje klasę alokatora dla obiekt multiset — typ  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `allocator_type` synonim parametru szablonu jest `Allocator`.  
  
 Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą `allocator_type`  
  
##  <a name="begin"></a>  multiset::BEGIN  
 Zwraca iteratora adresowania pierwszego elementu w zestawu wielokrotnego.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, adresowania pierwszego elementu w multiset lub lokalizacji pomyślne pustego zestawu wielokrotnego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_begin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::const_iterator ms1_cIter;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
   ms1.insert( 3 );  
  
   ms1_Iter = ms1.begin( );  
   cout << "The first element of ms1 is " << *ms1_Iter << endl;  
  
   ms1_Iter = ms1.begin( );  
   ms1.erase( ms1_Iter );  
  
   // The following 2 lines would err as the iterator is const  
   // ms1_cIter = ms1.begin( );  
   // ms1.erase( ms1_cIter );  
  
   ms1_cIter = ms1.begin( );  
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;  
}  
```  
  
```Output  
The first element of ms1 is 1  
The first element of ms1 is now 2  
```  
  
##  <a name="cbegin"></a>  multiset::cbegin  
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
  
##  <a name="cend"></a>  multiset::cend  
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
  
##  <a name="clear"></a>  multiset::Clear  
 Usuwa wszystkie elementy zestaw wielokrotny.  
  
```  
void clear();
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_clear.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
  
   cout << "The size of the multiset is initially "  
        << ms1.size( ) << "." << endl;  
  
   ms1.clear( );  
   cout << "The size of the multiset after clearing is "   
        << ms1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the multiset is initially 2.  
The size of the multiset after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  multiset::const_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element zestawu wielokrotnego.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) na przykład za pomocą `const_iterator`.  
  
##  <a name="const_pointer"></a>  multiset::const_pointer  
 Typ, który dostarcza wskaźnik do **const** element zestaw wielokrotny.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów zestawów wielokrotnych obiektu.  
  
##  <a name="const_reference"></a>  multiset::const_reference  
 Typ, który zawiera odwołanie do **const** element przechowywane w multiset do odczytu i wykonywania **const** operacji.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_const_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the multiset  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element zestawu wielokrotnego.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację multiset odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.  
  
##  <a name="count"></a>  multiset::Count  
 Zwraca liczbę elementów w multiset, którego klucz odpowiada parametr określony klucz.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz elementu do dopasowania z zestawu wielokrotnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w zestaw wielokrotny, którego klucz sortowania pasuje do parametru klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów *x* w zakresie  
  
 [ `lower_bound` (_ *Klucza* ), `upper_bound` (\_ *klucza* )).  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej multiset::count.  
  
```  
// multiset_count.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    multiset<int> ms1;  
    multiset<int>::size_type i;  
  
    ms1.insert(1);  
    ms1.insert(1);  
    ms1.insert(2);  
  
    // Elements do not need to be unique in multiset,  
    // so duplicates are allowed and counted.  
    i = ms1.count(1);  
    cout << "The number of elements in ms1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = ms1.count(2);  
    cout << "The number of elements in ms1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = ms1.count(3);  
    cout << "The number of elements in ms1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in ms1 with a sort key of 1 is: 2.  
The number of elements in ms1 with a sort key of 2 is: 1.  
The number of elements in ms1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>  multiset::crbegin  
 Zwraca const iteratora adresowania pierwszego elementu w odwróconej zestawu wielokrotnego.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszego elementu w odwróconej multiset lub adresowania co był ostatni element w stałe zestawu wielokrotnego.  
  
### <a name="remarks"></a>Uwagi  
 `crbegin` jest używany z odwróconej multiset podobnie jak rozpocząć jest używany zestaw wielokrotny.  
  
 Z wartością zwracaną z `crbegin`, multiset — obiektu nie może być modyfikowany.  
  
 `crbegin` może służyć do iterowania po zestaw wielokrotny Wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_crbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
```  
  
##  <a name="crend"></a>  multiset::crend  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multiset.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multiset (lokalizacja ma przed pierwszym elementem w stałe multiset).  
  
### <a name="remarks"></a>Uwagi  
 `crend` jest używany z odwróconej multiset podobnie jak [zakończenia](#end) jest używany zestaw wielokrotny.  
  
 Z wartością zwracaną z `crend`, multiset — obiektu nie może być modyfikowany.  
  
 `crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego zestawu wielokrotnego.  
  
 Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_crend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crend( ) ;  
   ms1_crIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
##  <a name="difference_type"></a>  multiset::difference_type  
 Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów w zakresie między elementami wskazywana przez Iteratory zestaw wielokrotny.  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakres elementów do , ale bez tego elementu wskazywanego przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez odwracalnego kontenerów, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępie swobodnym udostępniane przez kontener dostępie swobodnym, takich jak wektorowa.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;  
  
   ms1.insert( 20 );  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   ms1_bIter = ms1.begin( );  
   ms1_eIter = ms1.end( );  
  
   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );  
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );  
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );  
  
   // The keys, and hence the elements, of a multiset are not unique  
   cout << "The number '5' occurs " << df_typ5  
        << " times in multiset ms1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in multiset ms1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in multiset ms1.\n";  
  
   // Count the number of elements in a multiset   
   multiset <int>::difference_type  df_count = 0;  
   ms1_Iter = ms1.begin( );  
   while ( ms1_Iter != ms1_eIter)  
   {  
      df_count++;  
      ms1_Iter++;  
   }  
  
   cout << "The number of elements in the multiset ms1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in multiset ms1.  
The number '10' occurs 1 times in multiset ms1.  
The number '20' occurs 2 times in multiset ms1.  
The number of elements in the multiset ms1 is: 3.  
```  
  
##  <a name="emplace"></a>  multiset::emplace  
 Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane), ze wskazówką umieszczania.  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do zestawu wielokrotnego.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_emplace.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
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
    multiset<string> s1;  
  
    s1.emplace("Anna");  
    s1.emplace("Bob");  
    s1.emplace("Carmine");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
  
    s1.emplace("Bob");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a>  multiset::emplace_hint  
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
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do zestawu wielokrotnego.|  
|`where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.  
  
 Na przykład kod, zobacz [set::emplace_hint](../standard-library/set-class.md#emplace_hint).  
  
##  <a name="empty"></a>  multiset::Empty  
 Testy, jeśli zestaw wielokrotny, jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli multiset jest pusta. **false** Jeśli multiset nie jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_empty.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2;  
   ms1.insert ( 1 );  
  
   if ( ms1.empty( ) )  
      cout << "The multiset ms1 is empty." << endl;  
   else  
      cout << "The multiset ms1 is not empty." << endl;  
  
   if ( ms2.empty( ) )  
      cout << "The multiset ms2 is empty." << endl;  
   else  
      cout << "The multiset ms2 is not empty." << endl;  
}  
```  
  
```Output  
The multiset ms1 is not empty.  
The multiset ms2 is empty.  
```  
  
##  <a name="end"></a>  multiset::end  
 Zwraca iterator poza końcem.  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator przeszłości end. Jeśli zestaw wielokrotny, jest pusta, następnie `multiset::end() == multiset::begin()`.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora minął koniec jego zestawu wielokrotnego.  
  
 Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
 Na przykład kod, zobacz [multiset::find](#find).  
  
##  <a name="equal_range"></a>  multiset::equal_range  
 Zwraca parę Iteratory odpowiednio do pierwszego elementu w multiset za pomocą klucza, który jest większy niż określony klucz i pierwszy element w multiset za pomocą klucza jest równa lub większa niż klucz.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z multiset przeszukiwany elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para Iteratory tak, aby był pierwszy [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.  
  
 Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy**i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi**i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_equal_range.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;      
   typedef multiset<int, less<int> > IntSet;  
   IntSet ms1;  
   multiset <int> :: const_iterator ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;  
   p1 = ms1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.second ) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.first ) << "." << endl;  
  
   // Compare the upper_bound called directly   
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *ms1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = ms1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key less than 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key >= 40 is: "  
                << *( p1.first ) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.  
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The multiset ms1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  multiset::ERASE  
 Usuwa element lub zakres elementów w zestaw wielokrotny z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
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
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub element, który nie zawiera żadnego takiego elementu sygnalizuje koniec zestawu wielokrotnego.  
  
 Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z zestawu wielokrotnego.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład kod, zobacz [set::erase](../standard-library/set-class.md#erase).  
  
##  <a name="find"></a>  multiset::Find  
 Zwraca iteratora odnoszący się do lokalizacji elementu w zestaw wielokrotny, który ma klucz równoważne z określonym kluczem.  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza do dopasowania za pomocą klucza sortowania z multiset przeszukiwany elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora odnoszący się do lokalizacji element z określonym kluczem lub lokalizacji pomyślne wykonanie ostatniego elementu w multiset ( `multiset::end()`) Jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iterację odwołuje się do elementu w zestaw wielokrotny, którego klucz jest równoważne argumentowi `key` w obszarze binarny predykatu wywołujące kolejność oparte na mniej niż porównywalności relacji.  
  
 Jeśli wartość zwracana **znaleźć** jest przypisany do **const_iterator**, multiset — obiektu nie może być modyfikowany. Jeśli wartość zwracana **znaleźć** jest przypisany do **iteratora**, można zmodyfikować multiset — obiekt  
  
### <a name="example"></a>Przykład  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <set>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename T> void print_elem(const T& t) {  
    cout << "(" << t << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
template <typename C, class T> void findit(const C& c, T val) {  
    cout << "Trying find() on value " << val << endl;  
    auto result = c.find(val);  
    if (result != c.end()) {  
        cout << "Element found: "; print_elem(*result); cout << endl;  
    } else {  
        cout << "Element not found." << endl;  
    }  
}  
  
int main()  
{  
    multiset<int> s1({ 40, 45 });  
    cout << "The starting multiset s1 is: " << endl;  
    print_collection(s1);  
  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(41);  
    v.push_back(46);  
    v.push_back(42);  
    v.push_back(44);  
    v.push_back(44); // attempt a duplicate  
  
    cout << "Inserting the following vector data into s1: " << endl;  
    print_collection(v);  
  
    s1.insert(v.begin(), v.end());  
  
    cout << "The modified multiset s1 is: " << endl;  
    print_collection(s1);  
    cout << endl;  
    findit(s1, 45);  
    findit(s1, 6);  
}  
```  
  
##  <a name="get_allocator"></a>  multiset::get_allocator  
 Zwraca kopię obiektu alokatora użyty do utworzenia zestawu wielokrotnego.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez zestaw wielokrotny.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy multiset — Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_get_allocator.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int>::allocator_type ms1_Alloc;  
   multiset <int>::allocator_type ms2_Alloc;  
   multiset <double>::allocator_type ms3_Alloc;  
   multiset <int>::allocator_type ms4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   multiset <int> ms1;  
   multiset <int, allocator<int> > ms2;  
   multiset <double, allocator<double> > ms3;  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms3.max_size( ) <<  "." << endl;  
  
   // The following lines create a multiset ms4  
   // with the allocator of multiset ms1  
   ms1_Alloc = ms1.get_allocator( );  
   multiset <int> ms4( less<int>( ), ms1_Alloc );  
   ms4_Alloc = ms4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( ms1_Alloc == ms4_Alloc )     
   {  
      cout << "Allocators are interchangeable."  
           << endl;     
   }  
   else     
   {  
      cout << "Allocators are not interchangeable."  
           << endl;     
   }  
}  
```  
  
##  <a name="insert"></a>  multiset::INSERT  
 Wstawia element lub zakres elementów do zestawu wielokrotnego.  
  
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
|`Val`|Wartość elementu do wstawienia do zestawu wielokrotnego.|  
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `Where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|  
|`ValTy`|Parametr szablonu, który określa typ argumentu, który multiset można używać do tworzenia elementu [value_type](../standard-library/map-class.md#value_type), a idealnych przekazuje `Val` jako argument.|  
|`First`|Pozycja pierwszego elementu do skopiowania.|  
|`Last`|Pozycja poza ostatni element do skopiowania.|  
|`InputIterator`|Argument funkcji szablonu, który spełnia wymagania [wejściowych iteratora](../standard-library/input-iterator-tag-struct.md) wskazującego elementów typu, który może służyć do utworzenia [value_type](../standard-library/map-class.md#value_type) obiektów.|  
|`IList`|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcje Członkowskie jednym elementu wstawienie (1) i (2) zwraca iteratora miejsce, w którym wstawiono nowy element do zestawu wielokrotnego.  
  
 Funkcje Członkowskie pojedynczego elementu z wskazówki, (3) i (4) zwraca iterację, który wskazuje miejsce, w którym wstawiono nowy element do zestawu wielokrotnego.  
  
### <a name="remarks"></a>Uwagi  
 Brak wskaźniki lub odwołania jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.  
  
 Podczas wstawiania tylko jednego elementu jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wiele elementów jeśli wyjątek kontenera pozostaje w stanie nieokreślony, ale prawidłowy.  
  
 [Value_type](../standard-library/map-class.md#value_type) kontenera jest element typedef, który należy do kontenera i zestawu `multiset<V>::value_type` jest typem `const V`.  
  
 Zakres funkcji członkowskiej [5] wstawia sekwencji wartości elementów na zestaw wielokrotny odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja członkowska kontenera `end()` odwołuje się do położenia zaraz po ostatnim elementem w kontenerze — na przykład instrukcja `s.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `s`.  
  
 (6) używa funkcji członkowskiej liście inicjatorów [initializer_list](../standard-library/initializer-list.md) skopiuj elementy do zestawu wielokrotnego.  
  
 Do wstawienia elementu w miejscu skonstruować — to znaczy są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [multiset::emplace](#emplace) i [multiset::emplace_hint](#emplace_hint).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_insert.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
#include <string>  
#include <vector>  
  
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
  
    // insert single values   
    multiset<int> s1;  
    // call insert(const value_type&) version  
    s1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    s1.insert(20);  
  
    cout << "The original multiset values of s1 are:" << endl;  
    print(s1);  
  
    // intentionally attempt a duplicate, single element  
    s1.insert(1);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // single element, with hint  
    s1.insert(s1.end(), 30);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    multiset<int> s2;  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(294);  
    v.push_back(41);  
    v.push_back(330);  
    v.push_back(42);  
    v.push_back(45);  
  
    cout << "Inserting the following vector data into s2:" << endl;  
    print(v);  
  
    s2.insert(v.begin(), v.end());  
  
    cout << "The modified multiset values of s2 are:" << endl;  
    print(s2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    multiset<string>  s3;  
    string str1("blue"), str2("green");  
  
    // single element  
    s3.insert(move(str1));  
    cout << "After the first move insertion, s3 contains:" << endl;  
    print(s3);  
  
    // single element with hint  
    s3.insert(s3.end(), move(str2));  
    cout << "After the second move insertion, s3 contains:" << endl;  
    print(s3);  
    cout << endl;  
  
    multiset<int> s4;  
    // Insert the elements from an initializer_list  
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });  
    cout << "After initializer_list insertion, s4 contains:" << endl;  
    print(s4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a>  multiset::iterator  
 Typ, który zapewnia stałą [iteratora dwukierunkowego](../standard-library/bidirectional-iterator-tag-struct.md) który może odczytywać dowolny element w zestaw wielokrotny.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_comp"></a>  multiset::key_comp  
 Pobiera kopię obiektu porównania używany kolejność kluczy w zestaw wielokrotny.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiektu funkcja używaną do porządkowania jego elementów zestaw wielokrotny, który jest parametr szablonu `Compare`.  
  
 Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **const klucza &** *x*, **const klucza &** *y*);  
  
 która zwraca wartość true, jeśli *x* ściśle poprzedza *y* w kolejności sortowania.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu `Compare`. Oba typy są dostępne dla zestawu klas i zestaw wielokrotny, gdzie są one identyczne, aby zapewnić zgodność z mapowania klas i multimap, gdy są one różne.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_key_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of s1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of ms1."  
           << endl;  
   }  
  
   multiset <int, greater<int> > ms2;  
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.  
```  
  
##  <a name="key_compare"></a>  multiset::key_compare  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania w celu ustalenia względną kolejność dwa elementy zestawu wielokrotnego.  
  
```  
typedef Compare key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 **key_compare** jest synonimem parametru szablonu `Compare`.  
  
 Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="key_type"></a>  multiset::key_type  
 Typ, który udostępnia obiekt funkcji, które można porównać klucze sortowania w celu ustalenia względną kolejność dwa elementy zestawu wielokrotnego.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `key_type` synonim parametru szablonu jest `Key`.  
  
 Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.  
  
##  <a name="lower_bound"></a>  multiset::lower_bound  
 Zwraca iteratora do pierwszego elementu w zestaw wielokrotny za pomocą klucza, który jest równy lub większy niż określony klucz.  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z multiset przeszukiwany elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` lokalizacji elementu który adresów w zestaw wielokrotny, że za pomocą klucza, która jest równa lub większa niż klucz argumentu, lub który adresów lokalizacji pomyślne ostatniego elementu w zestaw wielokrotny, jeśli nie są zgodne Znaleziono dla klucza.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_lower_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.lower_bound( 20 );  
   cout << "The element of multiset ms1 with a key of 20 is: "  
        << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key of 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a derefenced iterator addressing the location  
   ms1_AcIter = ms1.end( );  
   ms1_AcIter--;  
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );  
   cout << "The element of ms1 with a key matching "  
        << "that of the last element is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of multiset ms1 with a key of 20 is: 20.  
The multiset ms1 doesn't have an element with a key of 40.  
The element of ms1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a>  multiset::max_size  
 Zwraca maksymalną długość zestawu wielokrotnego.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe zestawu wielokrotnego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_max_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::size_type i;  
  
   i = ms1.max_size( );     
   cout << "The maximum possible length "  
        << "of the multiset is " << i << "." << endl;  
}  
```  
  
##  <a name="multiset"></a>  multiset::multiset  
 Tworzy zestaw wielokrotny, który jest pusty lub kopii całości lub części innego zestawu wielokrotnego.  
  
```  
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,  
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp,   
    const Allocator& Al);

 
template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu zestaw wielokrotny, który domyślnie `Allocator`.|  
|`Comp`|Funkcja porównywania typu `const Compare` porządkowania elementów w zestaw wielokrotny, który domyślnie `Compare`.|  
|`Right`|Zestaw wielokrotny, który ma być kopii skonstruowane zestawu wielokrotnego.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Lista initializer_list, z której mają być skopiowane elementy.|  
  
### <a name="remarks"></a>Uwagi  
 Typ obiektu przydzielania, który zarządza przechowywania w pamięci dla multiset i który później może być zwracany przez wywołanie metody przechowywania wszystkie konstruktory [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.  
  
 Wszystkie konstruktory zainicjować ich zestawu wielokrotnego.  
  
 Wszystkie magazynu konstruktorów obiektem funkcji typu porównania, który jest używany do ustanawiania zamówienia wśród kluczy multiset i który później może być zwracany przez wywołanie metody [key_comp](#key_comp).  
  
 Określ pierwsze trzy konstruktorów pustego zestawu wielokrotnego początkowej, drugi określający typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów i trzeci jawne określenie programu przydzielania wpisz ( `Al`) do można użyć. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.  
  
 Konstruktor czwarty Określa kopię multiset `Right`.  
  
 Konstruktor piątej Określa kopię multiset przenosząc `Right`.  
  
 Szóstego, siódmego i ósmego konstruktorów Określ initializer_list, z którego można skopiować elementów.  
  
 Konstruktory trzech kolejnych skopiuj zakres `[First, Last)` multiset rosnącymi explicitness określania typu Funkcja porównywania i przydzielania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_ctor.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;  
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;  
  
    // Create an empty multiset ms0 of key type integer  
    multiset <int> ms0;  
  
    // Create an empty multiset ms1 with the key comparison  
    // function of less than, then insert 4 elements  
    multiset <int, less<int> > ms1;  
    ms1.insert(10);  
    ms1.insert(20);  
    ms1.insert(20);  
    ms1.insert(40);  
  
    // Create an empty multiset ms2 with the key comparison  
    // function of geater than, then insert 2 elements  
    multiset <int, less<int> > ms2;  
    ms2.insert(10);  
    ms2.insert(20);  
  
    // Create a multiset ms3 with the   
    // allocator of multiset ms1  
    multiset <int>::allocator_type ms1_Alloc;  
    ms1_Alloc = ms1.get_allocator();  
    multiset <int> ms3(less<int>(), ms1_Alloc);  
    ms3.insert(30);  
  
    // Create a copy, multiset ms4, of multiset ms1  
    multiset <int> ms4(ms1);  
  
    // Create a multiset ms5 by copying the range ms1[ first,  last)  
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;  
    ms1_bcIter = ms1.begin();  
    ms1_ecIter = ms1.begin();  
    ms1_ecIter++;  
    ms1_ecIter++;  
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);  
  
    // Create a multiset ms6 by copying the range ms4[ first,  last)  
    // and with the allocator of multiset ms2  
    multiset <int>::allocator_type ms2_Alloc;  
    ms2_Alloc = ms2.get_allocator();  
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);  
  
    cout << "ms1 =";  
    for (auto i : ms1)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms2 =";  
    for (auto i : ms2)  
        cout << " " << i;  
   cout << endl;  
  
   cout << "ms3 =";  
   for (auto i : ms3)  
       cout << " " << i;  
    cout << endl;  
  
    cout << "ms4 =";  
    for (auto i : ms4)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms5 =";  
    for (auto i : ms5)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms6 =";  
    for (auto i : ms6)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset by moving ms5  
    multiset<int> ms7(move(ms5));  
    cout << "ms7 =";  
    for (auto i : ms7)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset with an initializer_list  
    multiset<int> ms8({1, 2, 3, 4});  
    cout << "ms8=";  
    for (auto i : ms8)  
        cout << " " << i;  
    cout << endl;  
}  
```  
  
##  <a name="op_eq"></a>  multiset::operator =  
 Zastępuje elementy to `multiset` za pomocą elementów z innej `multiset`.  
  
```  
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|`multiset` Elementy, które są kopiowane lub przeniesione.|  
  
### <a name="remarks"></a>Uwagi  
 `operator=` kopiuje lub przenosi elementy `right` do tego `multiset`, w zależności od typu odwołanie (l-wartością lub r-wartości) używane. Elementy, które są w tym `multiset` przed `operator=` wykonuje zostaną odrzucone.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_operator_as.cpp  
// compile with: /EHsc  
#include <multiset>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   multiset<int> v1, v2, v3;  
   multiset<int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>  multiset::Pointer  
 Typ, który dostarcza wskaźnik do elementu w zestaw wielokrotny.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów zestawów wielokrotnych obiektu.  
  
##  <a name="rbegin"></a>  multiset::rbegin  
 Zwraca iteratora adresowania pierwszego elementu w odwróconej zestawu wielokrotnego.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego adresowania pierwszego elementu w odwróconej multiset lub adresowania co był ostatni element w stałe zestawu wielokrotnego.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z odwróconej zestaw wielokrotny, tak samo, jak rbegin jest używany zestaw wielokrotny.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, następnie multiset — obiektu nie może być modyfikowany. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu multiset —.  
  
 `rbegin` może służyć do iterowania po zestaw wielokrotny Wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_rbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // begin can be used to start an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is:";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << " " << *ms1_rIter;  
   cout << endl;  
  
   // A multiset element can be erased by dereferencing to its key   
   ms1_rIter = ms1.rbegin( );  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed multiset is "<< *ms1_rIter << "."   
        << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
The multiset is: 10 20 30  
The reversed multiset is: 30 20 10  
After the erasure, the first element in the reversed multiset is 20.  
```  
  
##  <a name="reference"></a>  multiset::Reference  
 Typ, który zawiera odwołanie do elementu przechowywane w zestaw wielokrotny.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="rend"></a>  multiset::rend  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej zestawu wielokrotnego.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multiset (lokalizacja ma przed pierwszym elementem w stałe multiset).  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z odwróconej multiset podobnie jak [zakończenia](#end) jest używany zestaw wielokrotny.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, następnie multiset — obiektu nie może być modyfikowany. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu multiset —.  
  
 `rend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego zestawu wielokrotnego.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_rend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rend( ) ;  
   ms1_rIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // end can be used to terminate an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is: ";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << *ms1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is: ";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << *ms1_rIter << " ";  
   cout << "." << endl;  
  
   ms1_rIter = ms1.rend( );  
   ms1_rIter--;  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rend( );  
   --ms1_rIter;  
   cout << "After the erasure, the last element in the "  
        << "reversed multiset is " << *ms1_rIter << "." << endl;  
}  
```  
  
##  <a name="reverse_iterator"></a>  multiset::reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej zestawu wielokrotnego.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` umożliwia iterację multiset odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="size"></a>  multiset::size  
 Zwraca liczbę elementów w multiset.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość zestawu wielokrotnego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: size_type i;  
  
   ms1.insert( 1 );  
   i = ms1.size( );  
   cout << "The multiset length is " << i << "." << endl;  
  
   ms1.insert( 2 );  
   i = ms1.size( );  
   cout << "The multiset length is now " << i << "." << endl;  
}  
```  
  
```Output  
The multiset length is 1.  
The multiset length is now 2.  
```  
  
##  <a name="size_type"></a>  multiset::size_type  
 Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w zestaw wielokrotny.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`  
  
##  <a name="swap"></a>  multiset::swap  
 Zamienia multisets dwa elementy.  
  
```  
void swap(
    multiset<Key, Compare, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Zestaw wielokrotny argumentu, zapewniając elementy, aby być zamieniona na multiset docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch multisets, której elementy są wymieniane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_swap.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2, ms3;  
   multiset <int>::iterator ms1_Iter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
   ms2.insert( 100 );  
   ms2.insert( 200 );  
   ms3.insert( 300 );  
  
   cout << "The original multiset ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the member function version of swap  
   ms1.swap( ms2 );  
  
   cout << "After swapping with ms2, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( ms1, ms3 );  
  
   cout << "After swapping with ms3, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original multiset ms1 is: 10 20 30.  
After swapping with ms2, list ms1 is: 100 200.  
After swapping with ms3, list ms1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  multiset::upper_bound  
 Zwraca iteratora do pierwszego elementu w zestaw wielokrotny za pomocą klucza, który jest większy niż określony klucz.  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z multiset przeszukiwany elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` który adresów lokalizacji elementu w zestaw wielokrotny za pomocą klucza jest większa niż klucz argumentu, lub że adresów lokalizacji pomyślne ostatniego elementu w zestaw wielokrotny, jeśli nie znaleziono dla klucz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_upper_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "The first element of multiset ms1 with a key greater "  
           << "than 20 is: " << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key greater than 30." << endl;  
   else  
      cout << "The element of multiset ms1 with a key > 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a dereferenced iterator addressing the location  
   ms1_AcIter = ms1.begin( );  
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );  
   cout << "The first element of ms1 with a key greater than"  
        << endl << "that of the initial element of ms1 is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of multiset ms1 with a key greater than 20 is: 30.  
The multiset ms1 doesn't have an element with a key greater than 30.  
The first element of ms1 with a key greater than  
that of the initial element of ms1 is: 20.  
```  
  
##  <a name="value_comp"></a>  multiset::value_comp  
 Pobiera kopię obiektu porównania służącą do wartości elementu kolejności w zestaw wielokrotny.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiektu funkcja używaną do porządkowania jego elementów zestaw wielokrotny, który jest parametr szablonu `Compare`.  
  
 Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **const klucza &**`_xVal`, **const klucza &**`_yVal`);  
  
 która zwraca wartość true, jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu `Compare`. Oba typy są dostępne dla zestawu klas i zestaw wielokrotny, gdzie są one identyczne, aby zapewnić zgodność z mapowania klas i multimap, gdy są one różne.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_value_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )     
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
   else     
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
  
   set <int, greater<int> > ms2;  
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )     
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.  
```  
  
##  <a name="value_compare"></a>  multiset::value_compare  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania w celu ustalenia, ich kolejność względną zestawu wielokrotnego.  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 `value_compare` synonim parametru szablonu jest `Compare`.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i **value_compare** są synonimy dla parametru szablonu `Compare`. Oba typy są dostępne dla zestawu klas i zestaw wielokrotny, gdzie są one identyczne, aby zapewnić zgodność z mapowania klas i multimap, gdy są one różne.  
  
 Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję uwag [multiset — klasa](../standard-library/multiset-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_comp](#value_comp) przykład sposobu deklarowanie i użycie `value_compare`.  
  
##  <a name="value_type"></a>  multiset::value_type  
 Typ, który opisuje obiekt zapisany jako elementu jako zestaw wielokrotny jako wartość.  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `value_type` synonim parametru szablonu jest `Key`.  
  
 Należy pamiętać, że oba [key_type](#key_type) i `value_type` są synonimy dla parametru szablonu **klucza**. Oba typy są dostępne dla zestawu klas i zestaw wielokrotny, gdzie są one identyczne, aby zapewnić zgodność z mapowania klas i multimap, gdy są one różne.  
  
 Aby uzyskać więcej informacji na temat `Key`, temacie w sekcji uwag.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// multiset_value_type.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
  
   multiset <int> :: value_type svt_Int;   // Declare value_type  
   svt_Int = 10;             // Initialize value_type  
  
   multiset <int> :: key_type skt_Int;   // Declare key_type  
   skt_Int = 20;             // Initialize key_type  
  
   ms1.insert( svt_Int );         // Insert value into s1  
   ms1.insert( skt_Int );         // Insert key into s1  
  
   // A multiset accepts key_types or value_types as elements  
   cout << "The multiset has elements:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The multiset has elements: 10 20.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Ustaw > elementy członkowskie](http://msdn.microsoft.com/en-us/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [Kontenery](../cpp/containers-modern-cpp.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

