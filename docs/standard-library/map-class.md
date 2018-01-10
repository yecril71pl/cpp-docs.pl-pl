---
title: "map — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
dev_langs: C++
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ce9135d298a0b80cedae87f20d65f4e012502cae
ms.sourcegitcommit: 0bbc9aac12c926b2b03726ae5b4a09d916e17d6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2017
---
# <a name="map-class"></a>map — Klasa
Używany do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania. Wartość klucza jest unikatowa i jest używana do automatycznego sortowania danych.  
  
 Można bezpośrednio zmienić wartość elementu w mapie. Wartość klucza jest stała i nie można jej zmienić. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza muszą zostać wstawione dla nowych elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key,   
    class Type,   
    class Traits = less<Key>,   
    class Allocator=allocator<pair <const Key, Type>>>  
class map;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Key`  
 Typ danych klucza, który ma być przechowywany w mapie.  
  
 `Type`  
 Typ danych elementu, który ma być przechowywany w mapie.  
  
 `Traits`  
 Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Ten argument jest opcjonalny i binarne predykatu `less<Key>` jest wartością domyślną.  
  
 W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając predykatu <> std::less, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji mapy i dezalokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair<const Key, Type> >`.  
  
## <a name="remarks"></a>Uwagi  
 Klasa map standardowa biblioteka C++ jest:  
  
-   Kontenerem o zmiennym rozmiarze, który skutecznie pobiera wartości elementów na podstawie skojarzonych wartości klucza.  
  
-   Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.  
  
-   Posortowana, ponieważ jej elementy są uporządkowane według wartości kluczy zgodnie z określoną funkcją porównywania.  
  
-   Unikatowy. ponieważ każdy z elementów musi mieć unikatowy klucz.  
  
-   Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.  
  
-   Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od typu elementu lub klucza. Typy danych, których można użyć dla elementów i kluczy, są określane jako parametry w szablonie klasy wraz z funkcją porównywania oraz alokatorem.  
  
 Iterator udostępnianym przez klasę mapy jest iteratora dwukierunkowego, ale [Wstaw](#insert) i [mapy](#map) funkcje elementu członkowskiego klasy mają wersje, które przyjmować jako parametry szablonu słabszych iteratora wejściowych, którego wymagania dotyczące funkcji jest mniej niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów są powiązane przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy, które z nim pracują, muszą być ograniczone przez te wymagania. Iterator danych wejściowych może zostać wyłuskany, aby odwołać się do jakiegoś obiektu, a także może być zwiększony do następnego iteratora w sekwencji.  
  
 Zalecamy, aby wybrać typ kontenera na podstawie rodzaju wyszukiwania i wstawiania, którego wymaga aplikacja. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, wykonują je w czasie najgorszego przypadku, który jest proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.  
  
 Zalecamy, aby kontener asocjacyjny z wyboru był mapą, gdy warunki, które kojarzą wartości z kluczami, są spełnione przez aplikację. Model dla tego rodzaju struktury jest uporządkowaną listą jednoznacznie występujących słów kluczowych mających skojarzone wartości ciągów, które zapewniają definicje. Jeśli wyraz ma więcej niż jedną poprawną definicję, tak że klucz nie jest unikatowy, wówczas mapa wielokrotnego dopasowania byłaby kontenerem z wyboru. Jeśli jest przechowywana tylko lista wyrazów, zestaw będzie odpowiednim kontenerem. Jeśli jest dozwolonych wiele wystąpień słów, to zestaw wielokrotny będzie odpowiedni.  
  
 Mapy Porządkuje elementy kontroluje przez wywołanie metody typu obiektu przechowywanej funkcji [key_compare](#key_compare). Ten obiekt przechowywanych jest funkcja porównywania, który jest dostępny przez wywołanie metody [key_comp](#key_comp) metody. Ogólnie rzecz biorąc, dowolne dwa dane elementy są porównywane, aby określić, czy jeden z nich jest mniejszy od drugiego lub czy są równoważne. W miarę porównywania wszystkich elementów, tworzona jest uporządkowana sekwencja nierównoważnych elementów.  
  
> [!NOTE]
>  Funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny f(x,y) predykatu jest obiektem funkcji, która ma dwa obiekty argument x i y, a wartością zwracaną `true` lub `false`. Kolejność na zestaw jest niska strict, kolejność czy binarny predykatu niezwrotne antysymetryczne dają w wyniku i przechodnie, a w przypadku przechodnie równoważność, gdy dwa obiekty x i y są zdefiniowane jako równoważne, gdy oba                     f (x, y) i f(y,x) `false`. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.  
>   
>  W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[mapy](#map)|Tworzy listę o określonym rozmiarze lub elementów określonej wartości na lub z określonym `allocator` lub jako kopię niektóre inne mapy.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Element typedef dla `allocator` klasy dla obiektu mapy.|  
|[const_iterator](#const_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytywać `const` element na mapie.|  
|[const_pointer](#const_pointer)|Element typedef dla wskaźnika do `const` element na mapie.|  
|[const_reference](#const_reference)|Element TypeDef stanowi odwołanie do `const` element przechowywane na mapie do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element na mapie.|  
|[difference_type](#difference_type)|Element typedef całkowitoliczbowy ze znakiem dla liczby elementów mapy w zakresie między elementami wskazywanymi przez iteratory.|  
|[iteratora](#iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować dowolny element w mapie.|  
|[key_compare](#key_compare)|Element typedef dla obiektu funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w mapie.|  
|[key_type](#key_type)|Element typedef dla klucza sortowania przechowywanego w każdym elemencie mapy.|  
|[mapped_type](#mapped_type)|Element typedef dla danych przechowywanych w każdym elemencie mapy.|  
|[wskaźnik](#pointer)|Element typedef dla wskaźnika do `const` element na mapie.|  
|[Odwołanie](#reference)|Element typedef dla odwołania do elementu przechowywanego w mapie.|  
|[reverse_iterator](#reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować element w odwróconej mapie.|  
|[size_type](#size_type)|Całkowitoliczbowy element typedef bez znaku określający liczbę elementów w mapie.|  
|[value_type](#value_type)|Element typedef dla typu obiektu przechowywanego jako element w mapie.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[w](#at)|Wyszukuje element z określoną wartością klucza.|  
|[Rozpocznij](#begin)|Zwraca iterator, który wskazuje na pierwszy element w mapie.|  
|[cbegin](#cbegin)|Zwraca iterator const, który wskazuje na pierwszy element w mapie.|  
|[cend](#cend)|Zwraca wartość const iteratora poza końcem.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy mapy.|  
|[Liczba](#count)|Zwraca liczbę elementów w mapie, których klucz pasuje do klucza określonego w parametrze.|  
|[crbegin](#crbegin)|Zwraca iterator const, który wskazuje na pierwszy element w odwróconej mapie.|  
|[crend](#crend)|Zwraca iterator const, który wskazuje na lokalizację po ostatnim elemencie w odwróconej mapie.|  
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do mapy.|  
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do mapy, ze wskazówką położenia.|  
|[pusty](#empty)|Zwraca `true` Jeśli mapy jest pusta.|  
|[koniec](#end)|Zwraca iterator poza końcem.|  
|[equal_range](#equal_range)|Zwraca parę iteratorów. Pierwszy iteratora w punktach pary do pierwszego elementu w `map` za pomocą klucza, który jest większy niż określony klucz. Drugi iteratora w punktach pary do pierwszego elementu w `map` za pomocą klucza jest równa lub większa niż klucz.|  
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w mapie z określonych pozycji.|  
|[Znajdź](#find)|Zwraca iterator, który wskazuje na pierwszą lokalizację elementu w mapie, który ma klucz równy określonemu kluczowi.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt, który jest używany do tworzenia mapy.|  
|[Wstaw](#insert)|Wstawia element lub zakres elementów do mapy na określonej pozycji.|  
|[key_comp](#key_comp)|Zwraca kopię obiektu porównania użytego do uporządkowania kluczy w mapie.|  
|[lower_bound —](#lower_bound)|Zwraca iterator do pierwszego elementu w mapie, którego wartość klucza jest równa lub większa od określonego klucza.|  
|[max_size](#max_size)|Zwraca maksymalną długość mapy.|  
|[rbegin](#rbegin)|Zwraca iterator, który wskazuje na pierwszy element w odwróconej mapie.|  
|[rend](#rend)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w odwróconej mapie.|  
|[rozmiar](#size)|Zwraca liczbę elementów w mapie.|  
|[swap](#swap)|Zamienia elementy z dwóch map.|  
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w mapie, którego wartość klucza jest większa od określonego klucza.|  
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w mapie.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Operator &#91; &#93;](#op_at)|Wstawia element do mapy z określoną wartością klucza.|  
|[operator =](#op_eq)|Zastępuje elementy mapy kopią innej mapy.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<mapy >  
  
 **Namespace:** Standard  
  
##  <a name="allocator_type"></a>map::allocator_type  
 Typ, który reprezentuje klasę alokatora dla obiekt mapy.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator) na przykład, który używa `allocator_type`.  
  
##  <a name="at"></a>map::AT  
 Wyszukuje element z określoną wartością klucza.  
  
```  
Type& at(const Key& key);

const Type& at(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`key`|Wartość klucza można znaleźć.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wartości danych znaleziono elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość klucza argument nie zostanie znaleziona, funkcja zwraca obiekt klasy [out_of_range — klasa](../standard-library/out-of-range-class.md).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_at.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
typedef std::map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// find and show elements  
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;   
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;   
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;   
  
    return (0);   
    }   
```  
  
##  <a name="begin"></a>map::BEGIN  
 Zwraca iteratora adresowania pierwszy element na mapie.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy element w mapie lub lokalizacji pomyślne pusta Mapa adresowania iteratora dwukierunkowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_begin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: const_iterator m1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 0, 0 ) );  
   m1.insert ( Int_Pair ( 1, 1 ) );  
   m1.insert ( Int_Pair ( 2, 4 ) );  
  
   m1_cIter = m1.begin ( );  
   cout << "The first element of m1 is " << m1_cIter -> first << endl;  
  
   m1_Iter = m1.begin ( );  
   m1.erase ( m1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // m1_cIter = m1.begin ( );  
   // m1.erase ( m1_cIter );  
  
   m1_cIter = m1.begin( );  
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;  
}  
```  
  
```Output  
The first element of m1 is 0  
The first element of m1 is now 1  
```  
  
##  <a name="cbegin"></a>map::cbegin  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dwukierunkowego pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu adresów (dla pustego zakresu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.  
  
 Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>map::cend  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dwukierunkowego dostępu, który wskazuje poza koniec zakresu.  
  
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
  
##  <a name="clear"></a>map::Clear  
 Usuwa wszystkie elementy mapy.  
  
```  
void clear();
```  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej map::clear.  
  
```  
// map_clear.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    m1.insert(Int_Pair(2, 4));  
  
    i = m1.size();  
    cout << "The size of the map is initially "  
         << i << "." << endl;  
  
    m1.clear();  
    i = m1.size();  
    cout << "The size of the map after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the map is initially 2.  
The size of the map after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>map::const_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element na mapie.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
 `const_iterator` Zdefiniowane przez punktów mapy dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair` \< **constKey**, **typu**> , którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.  
  
 Aby usunąć odwołania do `const_iterator` `cIter` wskazuje element na mapie, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `cIter`). **pierwszy**.  
  
 Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `cIter`  ->  **drugi**, który jest odpowiednikiem (\* `cIter`). **drugi**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) na przykład, który używa `const_iterator`.  
  
##  <a name="const_pointer"></a>map::const_pointer  
 Typ, który dostarcza wskaźnik do **const** element na mapie.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie mapy.  
  
##  <a name="const_reference"></a>map::const_reference  
 Typ, który zawiera odwołanie do **const** element przechowywane na mapie do odczytu i wykonywania **const** operacji.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_const_ref.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of first element in the map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of first element in the map is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the map is 1.  
The data value of first element in the map is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>map::const_reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element na mapie.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację mapy odwrotnie.  
  
 `const_reverse_iterator` Zdefiniowane przez punktów mapy dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair<const Key, Type>`, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.  
  
 Aby usunąć odwołania do `const_reverse_iterator crIter` wskazuje element na mapie, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `crIter`). **pierwszy**.  
  
 Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `crIter`  ->  **drugi**, który jest odpowiednikiem (\* `crIter`). **pierwszy**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.  
  
##  <a name="count"></a>map::Count  
 Zwraca liczbę elementów na mapie, którego klucz odpowiada parametr określony klucz.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza elementu do dopasowania z mapy.  
  
### <a name="return-value"></a>Wartość zwracana  
 1, jeśli mapy zawiera element, którego klucz sortowania pasuje do klucza parametr; 0, jeśli mapy nie zawierają element z odpowiedniego klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów *x* w zakresie  
  
 [ `lower_bound` (_ *Klucza* ), `upper_bound` (\_ *klucza* ))  
  
 która jest równa 0 lub 1 w przypadku mapa, która jest kontenerem asocjacyjnej unikatowy.  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej map::count.  
  
```  
// map_count.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    m1.insert(Int_Pair(2, 1));  
    m1.insert(Int_Pair(1, 4));  
    m1.insert(Int_Pair(2, 1));  
  
    // Keys must be unique in map, so duplicates are ignored  
    i = m1.count(1);  
    cout << "The number of elements in m1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = m1.count(2);  
    cout << "The number of elements in m1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = m1.count(3);  
    cout << "The number of elements in m1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in m1 with a sort key of 1 is: 1.  
The number of elements in m1 with a sort key of 2 is: 1.  
The number of elements in m1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>map::crbegin  
 Zwraca const iteratora adresowania pierwszy element na mapie odwróconej.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [mapy](../standard-library/map-class.md) lub adresowania co była ostatnim elementem w stałe `map`.  
  
### <a name="remarks"></a>Uwagi  
 `crbegin`jest używany z odwróconej `map` podobnie jak [rozpocząć](#begin) jest używany z `map`.  
  
 Z wartością zwracaną z `crbegin`, `map` obiektu nie może być modyfikowany.  
  
 `crbegin`może służyć do iterowania po `map` Wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_crbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crbegin( );  
   cout << "The first element of the reversed map m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed map m1 is 3.  
```  
  
##  <a name="crend"></a>map::crend  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w mapie odwróconej.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [mapy](../standard-library/map-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `map`).  
  
### <a name="remarks"></a>Uwagi  
 `crend`jest używany z mapą odwróconej podobnie jak [zakończenia](#end) jest używany z `map`.  
  
 Z wartością zwracaną z `crend`, `map` obiektu nie może być modyfikowany.  
  
 `crend`można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego `map`.  
  
 Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_crend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crend( );  
   m1_crIter--;  
   cout << "The last element of the reversed map m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed map m1 is 1.  
```  
  
##  <a name="difference_type"></a>map::difference_type  
 Typ liczbę całkowitą ze znakiem, służący do reprezentowania liczba elementów w zakresie między elementami wskazywana przez Iteratory mapy.  
  
```  
typedef allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie *[Imię, nazwisko)* między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakresu elementy do, z wyjątkiem, element wskazywana przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez kontenery odwracalny, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez udostępniane przez kontener dostępie swobodnym, takich jak wektorowa Iteratory dostępie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <map>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 3, 20 ) );  
   m1.insert ( Int_Pair ( 2, 30 ) );  
  
   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;  
   m1_bIter = m1.begin( );  
   m1_eIter = m1.end( );  
  
   // Count the number of elements in a map  
   map <int, int>::difference_type  df_count = 1;  
   m1_Iter = m1.begin( );  
   while ( m1_Iter != m1_eIter)  
   {  
      df_count++;  
      m1_Iter++;  
   }  
  
   cout << "The number of elements in the map m1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number of elements in the map m1 is: 4.  
```  
  
##  <a name="emplace"></a>map::emplace  
 Wstawia element zbudowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane) do mapy.  
  
```  
template <class... Args>  
pair<iterator, bool>  
emplace(
    Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do mapy, chyba że już zawiera element, którego wartość ekwiwalentnie porządkowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 A [pary](../standard-library/pair-structure.md) którego `bool` składnika ma wartość true, jeśli dokonano wstawiania i wartość false, jeśli mapy zawierają już element o równoważnej wartości w kolejności. Składnik iteratora pary wartość zwracaną wskazuje element nowo wstawionej Jeśli `bool` składnik jest wartość PRAWDA lub do istniejącego elementu Jeśli `bool` składników ma wartość false.  
  
 Aby uzyskać dostęp do składnika iteratora `pair` `pr`, użyj `pr.first`; Aby usunąć odwołania do niego, należy użyć `*pr.first`. Aby uzyskać dostęp do `bool` składnika, użyj `pr.second`. Na przykład zobacz przykładowy kod w dalszej części tego artykułu.  
  
### <a name="remarks"></a>Uwagi  
 Brak Iteratory lub odwołania jest nieważnych przez tę funkcję.  
  
 Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.  
  
 [Value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_emplace.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: ";  
  
    for (const auto& p : m) {  
        cout << "(" << p.first << ", " << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    map<int, string> m1;  
  
    auto ret = m1.emplace(10, "ten");  
  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Emplace failed, element with key 10 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
        cout << "map not modified" << endl;  
    }  
    else{  
        cout << "map modified, now contains ";  
        print(m1);  
    }  
    cout << endl;  
  
    ret = m1.emplace(10, "one zero");  
  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Emplace failed, element with key 10 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
    }  
    else{  
        cout << "map modified, now contains ";  
        print(m1);  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a>map::emplace_hint  
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
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do mapy, chyba że mapy zawiera już ten element lub ogólnie rzecz biorąc, chyba że jest on już zawiera element, którego klucz ekwiwalentnie porządkowania.|  
|`where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora do nowo wstawiony element.  
  
 Jeśli wstawiania nie powiodła się, ponieważ istnieje już element, zwraca iteratora istniejący element z kluczem.  
  
### <a name="remarks"></a>Uwagi  
 Brak Iteratory lub odwołania jest nieważnych przez tę funkcję.  
  
 Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.  
  
 [Value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_emplace.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: " << endl;  
  
    for (const auto& p : m) {  
        cout << "(" << p.first <<  "," << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    map<string, string> m1;  
  
    // Emplace some test data  
    m1.emplace("Anna", "Accounting");  
    m1.emplace("Bob", "Accounting");  
    m1.emplace("Carmine", "Engineering");  
  
    cout << "map starting data: ";  
    print(m1);  
    cout << endl;  
  
    // Emplace with hint  
    // m1.end() should be the "next" element after this emplacement  
    m1.emplace_hint(m1.end(), "Doug", "Engineering");  
  
    cout << "map modified, now contains ";  
    print(m1);  
    cout << endl;  
}  
  
```  
  
##  <a name="empty"></a>map::Empty  
 Testy, jeśli mapy jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli mapy jest pusta. **false** Jeśli mapy nie jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_empty.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2;  
  
   typedef pair <int, int> Int_Pair;  
   m1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( m1.empty( ) )  
      cout << "The map m1 is empty." << endl;  
   else  
      cout << "The map m1 is not empty." << endl;  
  
   if ( m2.empty( ) )  
      cout << "The map m2 is empty." << endl;  
   else  
      cout << "The map m2 is not empty." << endl;  
}  
```  
  
```Output  
The map m1 is not empty.  
The map m2 is empty.  
```  
  
##  <a name="end"></a>map::end  
 Zwraca iterator poza końcem.  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator przeszłości end. Jeśli mapy jest pusta, następnie `map::end() == map::begin()`.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnęła koniec jego mapy.  
  
 Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
 Na przykład kod, zobacz [map::find](#find).  
  
##  <a name="equal_range"></a>map::equal_range  
 Zwraca parę Iteratory reprezentujące [lower_bound](#lower_bound) klucza i [upper_bound](#upper_bound) klucza.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument wartość klucza ma zostać porównane z klucza sortowania elementu z tablicy, w którym wykonywane jest wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy**i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi**i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_equal_range.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
   typedef map <int, int, less<int> > IntMap;  
   IntMap m1;  
   map <int, int> :: const_iterator m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;  
   p1 = m1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2 in the map m1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2 in the map m1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   m1_RcIter = m1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << m1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = m1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of map m1 with a key >= 40 is: "  
           << p2.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2 in the map m1 is: 20.  
The upper bound of the element with a key of 2 in the map m1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The map m1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>map::ERASE  
 Usuwa element lub zakres elementów w mapie od określonej pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
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
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub element, który nie zawiera żadnego takiego elementu sygnalizuje koniec mapy.  
  
 Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z mapy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_erase.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
#include <iterator> // next() and prev() helper functions  
#include <utility>  // make_pair()  
  
using namespace std;  
  
using mymap = map<int, string>;  
  
void printmap(const mymap& m) {  
    for (const auto& elem : m) {  
        cout << " [" << elem.first << ", " << elem.second << "]";  
    }  
    cout << endl << "size() == " << m.size() << endl << endl;  
}  
  
int main()  
{  
    mymap m1;  
  
    // Fill in some data to test with, one at a time  
    m1.insert(make_pair(1, "A"));  
    m1.insert(make_pair(2, "B"));  
    m1.insert(make_pair(3, "C"));  
    m1.insert(make_pair(4, "D"));  
    m1.insert(make_pair(5, "E"));  
  
    cout << "Starting data of map m1 is:" << endl;  
    printmap(m1);  
    // The 1st member function removes an element at a given position  
    m1.erase(next(m1.begin()));  
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;  
    printmap(m1);  
  
    // Fill in some data to test with, one at a time, using an intializer list  
    mymap m2  
    {  
        { 10, "Bob" },  
        { 11, "Rob" },  
        { 12, "Robert" },  
        { 13, "Bert" },  
        { 14, "Bobby" }  
    };  
  
    cout << "Starting data of map m2 is:" << endl;  
    printmap(m2);  
    // The 2nd member function removes elements  
    // in the range [First, Last)  
    m2.erase(next(m2.begin()), prev(m2.end()));  
    cout << "After the middle elements are deleted, the map m2 is:" << endl;  
    printmap(m2);  
  
    mymap m3;  
  
    // Fill in some data to test with, one at a time, using emplace  
    m3.emplace(1, "red");  
    m3.emplace(2, "yellow");  
    m3.emplace(3, "blue");  
    m3.emplace(4, "green");  
    m3.emplace(5, "orange");  
    m3.emplace(6, "purple");  
    m3.emplace(7, "pink");  
  
    cout << "Starting data of map m3 is:" << endl;  
    printmap(m3);  
    // The 3rd member function removes elements with a given Key  
    mymap::size_type count = m3.erase(2);  
    // The 3rd member function also returns the number of elements removed  
    cout << "The number of elements removed from m3 is: " << count << "." << endl;  
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;  
    printmap(m3);  
}  
  
```  
  
##  <a name="find"></a>map::Find  
 Zwraca iteratora odnoszący się do lokalizacji elementu na mapie, który ma klucz równoważne z określonym kluczem.  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza do dopasowania za pomocą klucza sortowania elementu z tablicy, w którym wykonywane jest wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora odnoszący się do lokalizacji element z określonym kluczem lub lokalizacji pomyślne ostatni element w mapie ( `map::end()`) Jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora odnoszący się do elementu w planie, którego klucz sortowania jest odpowiednikiem klucza argument w predykat binarne wywołujące kolejność oparte na mniej niż porównywalności relacji.  
  
 Jeśli wartość zwracana **znaleźć** jest przypisany do **const_iterator**, nie można zmodyfikować obiektu mapy. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, można zmodyfikować obiektu mapy  
  
### <a name="example"></a>Przykład  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <map>  
#include <iostream>  
#include <vector>  
#include <string>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename A, typename B> void print_elem(const pair<A, B>& p) {  
    cout << "(" << p.first << ", " << p.second << ") ";  
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
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });  
    cout << "The starting map m1 is (key, value):" << endl;  
    print_collection(m1);  
  
    vector<pair<int, string>> v;  
    v.push_back(make_pair(43, "Tc"));  
    v.push_back(make_pair(41, "Nb"));  
    v.push_back(make_pair(46, "Pd"));  
    v.push_back(make_pair(42, "Mo"));  
    v.push_back(make_pair(44, "Ru"));  
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate  
  
    cout << "Inserting the following vector data into m1:" << endl;  
    print_collection(v);  
  
    m1.insert(v.begin(), v.end());  
  
    cout << "The modified map m1 is (key, value):" << endl;  
    print_collection(m1);  
    cout << endl;  
    findit(m1, 45);  
    findit(m1, 6);  
}  
  
```  
  
##  <a name="get_allocator"></a>map::get_allocator  
 Zwraca kopię obiektu alokatora użyty do utworzenia mapy.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez mapy.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy mapy Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_get_allocator.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int>::allocator_type m1_Alloc;  
   map <int, int>::allocator_type m2_Alloc;  
   map <int, double>::allocator_type m3_Alloc;  
   map <int, int>::allocator_type m4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   map <int, int> m1;  
   map <int, int, allocator<int> > m2;  
   map <int, double, allocator<double> > m3;  
  
   m1_Alloc = m1.get_allocator( );  
   m2_Alloc = m2.get_allocator( );  
   m3_Alloc = m3.get_allocator( );  
  
   cout << "The number of integers that can be allocated\n"  
        << "before free memory is exhausted: "  
        << m2.max_size( ) << ".\n" << endl;  
  
   cout << "The number of doubles that can be allocated\n"  
        << "before free memory is exhausted: "  
        << m3.max_size( ) <<  ".\n" << endl;  
  
   // The following line creates a map m4  
   // with the allocator of map m1.  
   map <int, int> m4( less<int>( ), m1_Alloc );  
  
   m4_Alloc = m4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( m1_Alloc == m4_Alloc )     
   {  
      cout << "The allocators are interchangeable." << endl;  
   }  
   else     
   {  
      cout << "The allocators are not interchangeable." << endl;  
   }  
}  
```  
  
##  <a name="insert"></a>map::INSERT  
 Wstawia element lub zakres elementów do mapy.  
  
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
|`Val`|Wartość elementu ma zostać wstawiony do mapy, chyba że już zawiera element, którego klucz ekwiwalentnie porządkowania.|  
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `Where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|  
|`ValTy`|Parametr szablonu, który określa typ argumentu, który mapy można używać do tworzenia elementu [value_type](#value_type), a idealnych przekazuje `Val` jako argument.|  
|`First`|Pozycja pierwszego elementu do skopiowania.|  
|`Last`|Pozycja poza ostatni element do skopiowania.|  
|`InputIterator`|Argument funkcji szablonu, który spełnia wymagania [wejściowych iteratora](../standard-library/input-iterator-tag-struct.md) wskazującego elementów typu, który może służyć do utworzenia [value_type](#value_type) obiektów.|  
|`IList`|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcje Członkowskie pojedynczego elementu (1) i (2) zwracają [pary](../standard-library/pair-structure.md) którego `bool` składnik jest wartość true, jeśli dokonano wstawiania i wartość false, jeśli mapy już zawiera element, którego klucz ma wartość równoważną w kolejności. Składnik iteratora pary wartość zwracaną wskazuje element nowo wstawionej Jeśli `bool` składnik jest wartość PRAWDA lub do istniejącego elementu Jeśli `bool` składników ma wartość false.  
  
 Funkcje Członkowskie pojedynczego elementu z wskazówki, (3) i (4) zwraca iteratora wskazującą położenie w przypadku, gdy nowy element została umieszczona w mapie lub, jeśli element z kluczem odpowiednik już istnieje, do istniejącego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Nie Iteratory, wskaźniki lub odwołania jest nieważnych przez tę funkcję.  
  
 Podczas wstawiania tylko jednego elementu jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wiele elementów jeśli wyjątek kontenera pozostaje w stanie nieokreślony, ale prawidłowy.  
  
 Aby uzyskać dostęp do składnika iteratora `pair` `pr` który jest zwracany za pomocą funkcji pojedynczego elementu członkowskiego, użyj `pr.first`; aby wyłuskania iteratora w pary zwrócone, użyj `*pr.first`, umożliwiając elementu. Aby uzyskać dostęp do `bool` składnika, użyj `pr.second`. Na przykład zobacz przykładowy kod w dalszej części tego artykułu.  
  
 [Value_type](#value_type) kontenera jest element typedef, który należy do kontenera i mapy, `map<K, V>::value_type` jest `pair<const K, V>`. Wartość elementu jest uporządkowana pary, w którym znajduje się pierwszy składnik jest równa wartości klucza, a drugi składnik jest równa wartości danych elementu.  
  
 Zakres funkcji członkowskiej [5] wstawia sekwencji wartości elementów do mapy odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja członkowska kontenera `end()` odwołuje się do położenia zaraz po ostatnim elementem w kontenerze — na przykład instrukcja `m.insert(v.begin(), v.end());` próba wstawienia wszystkie elementy `v` do `m`. Tylko elementy, które mają unikatowe wartości w zakresie są wstawiane; duplikaty są ignorowane. Aby sprawdzić, które elementy zostały odrzucone, użyj wersji pojedynczego elementu `insert`.  
  
 (6) używa funkcji członkowskiej liście inicjatorów [initializer_list](../standard-library/initializer-list.md) skopiuj elementy do mapy.  
  
 Do wstawienia elementu w miejscu skonstruować — to znaczy są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [map::emplace](#emplace) i [map::emplace_hint](#emplace_hint).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_insert.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
#include <vector>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: ";  
  
    for (const auto& p : m) {  
        cout << "(" << p.first << ", " << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
  
    // insert single values   
    map<int, int> m1;  
    // call insert(const value_type&) version  
    m1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    m1.insert(make_pair(2, 20));  
  
    cout << "The original key and mapped values of m1 are:" << endl;  
    print(m1);  
  
    // intentionally attempt a duplicate, single element  
    auto ret = m1.insert(make_pair(1, 111));  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Insert failed, element with key value 1 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
    }  
    else{  
        cout << "The modified key and mapped values of m1 are:" << endl;  
        print(m1);  
    }  
    cout << endl;  
  
    // single element, with hint  
    m1.insert(m1.end(), make_pair(3, 30));  
    cout << "The modified key and mapped values of m1 are:" << endl;  
    print(m1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    map<int, int> m2;  
    vector<pair<int, int>> v;  
    v.push_back(make_pair(43, 294));  
    v.push_back(make_pair(41, 262));  
    v.push_back(make_pair(45, 330));  
    v.push_back(make_pair(42, 277));  
    v.push_back(make_pair(44, 311));  
  
    cout << "Inserting the following vector data into m2:" << endl;  
    print(v);  
  
    m2.insert(v.begin(), v.end());  
  
    cout << "The modified key and mapped values of m2 are:" << endl;  
    print(m2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    map<int, string>  m3;  
    pair<int, string> ip1(475, "blue"), ip2(510, "green");  
  
    // single element  
    m3.insert(move(ip1));  
    cout << "After the first move insertion, m3 contains:" << endl;  
    print(m3);  
  
    // single element with hint  
    m3.insert(m3.end(), move(ip2));  
    cout << "After the second move insertion, m3 contains:" << endl;  
    print(m3);  
    cout << endl;  
  
    map<int, int> m4;  
    // Insert the elements from an initializer_list  
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });  
    cout << "After initializer_list insertion, m4 contains:" << endl;  
    print(m4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a>map::iterator  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element na mapie.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 **Iterator** zdefiniowane przez punktów mapy dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair`  *\<*  **constKey** , **Typu***>*, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.  
  
 Aby usunąć odwołania do **iterator** `Iter` wskazuje element na mapie, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter`  ->  **pierwszy**, który jest odpowiednikiem (\* `Iter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `Iter`  ->  **drugi**, który jest odpowiednikiem (\* `Iter`). **drugi**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_comp"></a>map::key_comp  
 Pobiera kopię porównania obiekt używany do kluczy zamówienia na mapie.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcja używaną do porządkowania jego elementów mapy.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego  
  
 **bool operator**( **constKey &**`left`, **const klucza &**`right`);  
  
 która zwraca **true** Jeśli `left` poprzedza i nie jest równa `right` w kolejności sortowania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_key_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   map <int, int, less<int> > m1;  
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
  
   map <int, int, greater<int> > m2;  
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.  
```  
  
##  <a name="key_compare"></a>map::key_compare  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwa elementy na mapie.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 `key_compare`synonim parametru szablonu jest `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [map — klasa](../standard-library/map-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="key_type"></a>map::key_type  
 Typ, który opisuje klucza sortowania przechowywane w każdym elemencie mapy.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `key_type`synonim parametru szablonu jest `Key`.  
  
 Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [map — klasa](../standard-library/map-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.  
  
##  <a name="lower_bound"></a>map::lower_bound  
 Zwraca pierwszy element na mapie o wartości klucza, który jest równy lub większy niż określony klucz iteratora.  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument wartość klucza ma zostać porównane z klucza sortowania elementu z tablicy, w którym wykonywane jest wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` czy adresy lokalizacji elementu na mapie, że za pomocą klucza, która jest równa lub większa niż klucz argumentu, lub które adresów lokalizacji pomyślne ostatnim elementem w planie, jeśli nie są zgodne, został znaleziony dla klucz.  
  
 Jeśli wartość zwracana `lower_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu mapy. Jeśli wartość zwracana `lower_bound` jest przypisany do **iterator**, można zmodyfikować obiektu mapy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_lower_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_RcIter = m1.lower_bound( 2 );  
   cout << "The first element of map m1 with a key of 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for this key, end( ) is returned  
   m1_RcIter = m1. lower_bound ( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of map m1 with a key of 4 is: "  
           << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the map can be found   
   // using a dereferenced iterator addressing the location  
   m1_AcIter = m1.end( );  
   m1_AcIter--;  
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );  
   cout << "The element of m1 with a key matching "  
        << "that of the last element is: "  
        << m1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of map m1 with a key of 2 is: 20.  
The map m1 doesn't have an element with a key of 4.  
The element of m1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="map"></a>map::map  
 Tworzy mapę, który jest pusty lub kopii całości lub części niektóre inne mapy.  
  
```  
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,  
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,  
    const Traits& Comp);

map(
    initializer_list<value_type> IList,  
    const Traits& Comp,   
    const Allocator& Allocator);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu mapy, która domyślnie określa `Allocator`.|  
|`Comp`|Funkcja porównywania typu `const Traits` porządkowania elementów w tablicy, która domyślnie określa `hash_compare`.|  
|`Right`|Mapy skonstruowane zestawu ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Initializer_list, z którego mają zostać skopiowane elementy.|  
  
### <a name="remarks"></a>Uwagi  
 Typ obiektu przydzielania, który zarządza mapy przechowywania w pamięci i który później może być zwracany przez wywołanie metody przechowywania wszystkie konstruktory [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.  
  
 Wszystkie konstruktory zainicjować ich mapy.  
  
 Wszystkie konstruktory przechowywania obiektem funkcji typu cech, który jest używany do ustanawiania zamówienia wśród kluczy mapy i który później może być zwracany przez wywołanie metody [key_comp](#key_comp).  
  
 Określ pierwsze trzy konstruktorów pusta Mapa początkowej, drugi określający typ porównania funkcji ( `Comp`) ma być używana podczas ustanawiania kolejność elementów, a trzeci jawne określenie programu przydzielania wpisz ( `Al`) jako używane. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.  
  
 Konstruktor czwarty Określa kopię mapy `Right`.  
  
 Konstruktor piątej Określa kopię mapy przenosząc `Right`.  
  
 Szóstego, siódmego i ósmego konstruktorów Użyj initializer_list, z którego można skopiować elementów członkowskich.  
  
 Konstruktory trzech kolejnych skopiuj zakres `[First, Last)` mapy rosnącymi explicitness określania typu porównanie funkcji klasy `Traits` i przydzielania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_map.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    typedef pair <int, int> Int_Pair;  
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;  
    map <int, int, less<int> >::iterator m2_Iter;  
  
    // Create an empty map m0 of key type integer  
    map <int, int> m0;  
  
    // Create an empty map m1 with the key comparison  
    // function of less than, then insert 4 elements  
    map <int, int, less<int> > m1;  
    m1.insert(Int_Pair(1, 10));  
    m1.insert(Int_Pair(2, 20));  
    m1.insert(Int_Pair(3, 30));  
    m1.insert(Int_Pair(4, 40));  
  
    // Create an empty map m2 with the key comparison  
    // function of geater than, then insert 2 elements  
    map <int, int, less<int> > m2;  
    m2.insert(Int_Pair(1, 10));  
    m2.insert(Int_Pair(2, 20));  
  
    // Create a map m3 with the   
    // allocator of map m1  
    map <int, int>::allocator_type m1_Alloc;  
    m1_Alloc = m1.get_allocator();  
    map <int, int> m3(less<int>(), m1_Alloc);  
    m3.insert(Int_Pair(3, 30));  
  
    // Create a copy, map m4, of map m1  
    map <int, int> m4(m1);  
  
    // Create a map m5 by copying the range m1[ first,  last)  
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;  
    m1_bcIter = m1.begin();  
    m1_ecIter = m1.begin();  
    m1_ecIter++;  
    m1_ecIter++;  
    map <int, int> m5(m1_bcIter, m1_ecIter);  
  
    // Create a map m6 by copying the range m4[ first,  last)  
    // and with the allocator of map m2  
    map <int, int>::allocator_type m2_Alloc;  
    m2_Alloc = m2.get_allocator();  
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);  
  
    cout << "m1 =";  
    for (auto i : m1)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m2 =";  
    for(auto i : m2)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m3 =";  
    for (auto i : m3)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m4 =";  
    for (auto i : m4)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m5 =";  
    for (auto i : m5)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m6 =";  
    for (auto i : m6)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m7 by moving m5  
    cout << "m7 =";  
    map<int, int> m7(move(m5));  
    for (auto i : m7)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m8 by copying in an initializer_list  
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };  
    cout << "m8: = ";  
    for (auto i : m8)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m9 with an initializer_list and a comparator  
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());  
    cout << "m9: = ";  
    for (auto i : m9)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m10 with an initializer_list, a comparator, and an allocator  
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());  
    cout << "m10: = ";  
    for (auto i : m10)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
}  
  
```  
  
##  <a name="mapped_type"></a>map::mapped_type  
 Typ, który reprezentuje dane przechowywane na mapie.  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `mapped_type` jest synonimem klasy `Type` parametru szablonu.  
  
 Aby uzyskać więcej informacji na temat `Type` zobacz [map — klasa](../standard-library/map-class.md) tematu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `mapped_type`.  
  
##  <a name="max_size"></a>map::max_size  
 Zwraca maksymalną długość mapy.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe mapy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_max_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   map <int, int> :: size_type i;  
  
   i = m1.max_size( );  
   cout << "The maximum possible length "  
        << "of the map is " << i << "."  
        << endl << "(Magnitude is machine specific.)";  
}  
```  
  
##  <a name="op_at"></a>map::operator]  
 Wstawia element do mapy z określoną wartością klucza.  
  
```  
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`key`|Wartość klucza elementu, który ma zostać wstawiony.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wartości danych wstawionego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.  
  
 `operator[]`może służyć do wstawienia elementów do mapy `m` przy użyciu `m[ key] = DataValue;` gdzie `DataValue` jest wartością `mapped_type` elementu o wartości klucza `key`.  
  
 Korzystając z `operator[]` wstawianie elementów, zwracane odwołanie nie wskazuje, czy wstawiania jest zmiana istniejącego elementu lub tworzenia nowej. Funkcje Członkowskie [znaleźć](#find) i [Wstaw](#insert) może służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_op_insert.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   typedef pair <const int, int> cInt2Int;  
   map <int, int> m1;  
   map <int, int> :: iterator pIter;  
  
   // Insert a data value of 10 with a key of 1  
   // into a map using the operator[] member function  
   m1[ 1 ] = 10;  
  
   // Compare other ways to insert objects into a map  
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );  
   m1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // If the key already exists, operator[]  
   // changes the value of the datum in the element  
   m1[ 2 ] = 40;  
  
   // operator[] will also insert the value of the data  
   // type's default constructor if the value is unspecified  
   m1[5];  
  
   cout  << "The keys of the mapped elements are now:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are now:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
// insert by moving key  
    map<string, int> c2;  
    string str("abc");  
    cout << "c2[move(str)] == " << c2[move(str)] << endl;  
    cout << "c2["abc"] == " << c2["abc"] << endl;  
  
    return (0);   
}  
```  
  
```Output  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 30.  
The keys of the mapped elements are now: 1 2 3 5.  
The values of the mapped elements are now: 10 40 30 0.  
c2[move(str)] == 0  
c2["abc"] == 1  
```  
  
##  <a name="op_eq"></a>map::operator =  
 Zastępuje elementy mapy kopią innej mapy.  
  
```  
map& operator=(const map& right);

map& operator=(map&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Mapy](../standard-library/map-class.md) kopiowane do `map`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `map`, `operator=` albo kopiuje lub przenosi zawartość `right` do mapy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_operator_as.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   map<int, int> v1, v2, v3;  
   map<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>map::Pointer  
 Typ, który dostarcza wskaźnik do elementu na mapie.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie mapy.  
  
##  <a name="rbegin"></a>map::rbegin  
 Zwraca iteratora adresowania pierwszy element na mapie odwróconej.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego adresowania pierwszy element na mapie odwróconej lub adresowania co był ostatni element w mapie stałe.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin`jest używany z mapą odwróconej podobnie jak [rozpocząć](#begin) jest używany z mapą.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, a następnie obiektu mapy nie może być modyfikowany. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu mapy.  
  
 `rbegin`może służyć do iterowania po mapy Wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_rbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: reverse_iterator m1_rIter;  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rbegin( );  
   cout << "The first element of the reversed map m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a map in a forward order  
   cout << "The map is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a map in a reverse order  
   cout << "The reversed map is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A map element can be erased by dereferencing to its key   
   m1_rIter = m1.rbegin( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed map is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed map m1 is 3.  
The map is: 1 2 3 .  
The reversed map is: 3 2 1 .  
After the erasure, the first element in the reversed map is 2.  
```  
  
##  <a name="reference"></a>map::Reference  
 Typ, który zawiera odwołanie do elementu przechowywane na mapie.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_reference.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of first element in the map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of first element in the map is "  
        << Ref2 << "." << endl;  
  
   //The non-const_reference can be used to modify the   
   //data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the map is 1.  
The data value of first element in the map is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>map::rend  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w mapie odwróconej.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w mapie odwróconej (lokalizacja ma przed pierwszym elementem w planie stałe).  
  
### <a name="remarks"></a>Uwagi  
 `rend`jest używany z mapą odwróconej podobnie jak [zakończenia](#end) jest używany z mapą.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, a następnie obiektu mapy nie może być modyfikowany. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu mapy.  
  
 `rend`można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego mapy.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_rend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: reverse_iterator m1_rIter;  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "The last element of the reversed map m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a map in a forward order  
   cout << "The map is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a map in a reverse order  
   cout << "The reversed map is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A map element can be erased by dereferencing to its key   
   m1_rIter = --m1.rend( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed map is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed map m1 is 1.  
The map is: 1 2 3 .  
The reversed map is: 3 2 1 .  
After the erasure, the last element in the reversed map is 2.  
```  
  
##  <a name="reverse_iterator"></a>map::reverse_iterator  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować element w mapie odwróconej.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację mapy odwrotnie.  
  
 `reverse_iterator` Zdefiniowane przez punktów mapy dla elementów, które są obiektami [value_type](#value_type), która jest typu `pair`  *\<*  **constKey**,  **Typ***>*, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.  
  
 Aby usunąć odwołania do `reverse_iterator` `rIter` wskazuje element na mapie, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `rIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `rIter`  ->  **drugi**, który jest odpowiednikiem (\* `rIter`). **pierwszy**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="size"></a>map::size  
 Zwraca liczbę elementów w mapie.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość mapy.  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej map::size.  
  
```  
// map_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1, m2;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    i = m1.size();  
    cout << "The map length is " << i << "." << endl;  
  
    m1.insert(Int_Pair(2, 4));  
    i = m1.size();  
    cout << "The map length is now " << i << "." << endl;  
}  
```  
  
```Output  
The map length is 1.  
The map length is now 2.  
```  
  
##  <a name="size_type"></a>map::size_type  
 Typ liczby całkowitej bez znaku, który może reprezentować liczby elementów na mapie.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`.  
  
##  <a name="swap"></a>map::swap  
 Zamienia elementy z dwóch map.  
  
```  
void swap(
    map<Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Mapa argumentu, zapewniając elementy, aby być zamieniona na docelowa mapa.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch mapy, której elementy są wymieniane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_swap.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3;  
   map <int, int>::iterator m1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
   m2.insert ( Int_Pair ( 10, 100 ) );  
   m2.insert ( Int_Pair ( 20, 200 ) );  
   m3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   //m2 is said to be the argument map; m1 the target map  
   m1.swap( m2 );  
  
   cout << "After swapping with m2, map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( m1, m3 );  
  
   cout << "After swapping with m3, map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original map m1 is: 10 20 30.  
After swapping with m2, map m1 is: 100 200.  
After swapping with m3, map m1 is: 300.  
```  
  
##  <a name="upper_bound"></a>map::upper_bound  
 Zwraca iteratora pierwszy element na mapie, że za pomocą klucza o wartości, która jest większy niż określony klucz.  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza argument ma być porównywana z wartością klucza sortowania elementu z tablicy, w którym wykonywane jest wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` czy adresy lokalizacji elementu na mapie, że za pomocą klucza jest większa niż klucz argumentu, lub że adresów lokalizacji pomyślne ostatnim elementem w planie, jeśli nie są zgodne znajduje się dla klucza.  
  
 Jeśli wartość zwracana jest przypisany do `const_iterator`, nie można zmodyfikować obiektu mapy. Jeśli wartość zwracana jest przypisany do **iterator**, można zmodyfikować obiektu mapy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_upper_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_RcIter = m1.upper_bound( 2 );  
   cout << "The first element of map m1 with a key "  
        << "greater than 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end is returned  
   m1_RcIter = m1. upper_bound ( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key greater than 4." << endl;  
   else  
      cout << "The element of map m1 with a key > 4 is: "  
           << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the map can be found   
   // using a dereferenced iterator addressing the location  
   m1_AcIter = m1.begin( );  
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );  
   cout << "The 1st element of m1 with a key greater than\n"  
        << "that of the initial element of m1 is: "  
        << m1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of map m1 with a key greater than 2 is: 30.  
The map m1 doesn't have an element with a key greater than 4.  
The 1st element of m1 with a key greater than  
that of the initial element of m1 is: 20.  
```  
  
##  <a name="value_comp"></a>map::value_comp  
 Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów na mapie, porównując wartości klucza.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcja porównania, używaną do porządkowania jego elementów mapy.  
  
### <a name="remarks"></a>Uwagi  
 Mapy *m*, jeśli dwa elementy *e*1 ( *k*1, *d*1) i *e*2 ( *k*2, `d`2) obiekty typu `value_type`, gdzie *k*1 i *k*2 są ich kluczy typu `key_type` i `d`1 i `d`są 2 dane typu `mapped_type`, następnie *m.*`value_comp`( *e*1, *e*2) jest odpowiednikiem *m.* `key_comp` *(k*1, *k*2). Obiekt przechowywanych definiuje funkcję elementu członkowskiego  
  
 **bool operator**( **value_type &**`left`, **value_type &**`right`);  
  
 która zwraca **true** Jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w kolejności sortowania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_value_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   map <int, int, less<int> > m1;  
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
  
   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );  
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *pr1.first, *pr2.first ) == true )     
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if(vc1( *pr2.first, *pr1.first ) == true )  
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
```Output  
The element ( 1,10 ) precedes the element ( 2,5 ).  
The element ( 2,5 ) does not precede the element ( 1,10 ).  
```  
  
##  <a name="value_type"></a>map::value_type  
 Typ obiektu przechowywane jako element na mapie.  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// map_value_type.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef pair <const int, int> cInt2Int;  
   map <int, int> m1;  
   map <int, int> :: key_type key1;  
   map <int, int> :: mapped_type mapped1;  
   map <int, int> :: value_type value1;  
   map <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitly to avoid implicit type conversion  
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare other ways to insert objects into a map  
   m1.insert ( cInt2Int ( 2, 20 ) );  
   m1[ 3 ] = 30;  
  
   // Initializing key1 and mapped1  
   key1 = ( m1.begin( ) -> first );  
   mapped1 = ( m1.begin( ) -> second );  
  
   cout << "The key of first element in the map is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the map is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Mapa > elementy członkowskie](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [Kontenery](../cpp/containers-modern-cpp.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)
