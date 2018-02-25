---
title: "hash_multiset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78fb4998754bc7a4b30a63de166973909d21b68f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="hashmultiset-class"></a>hash_multiset — Klasa
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Hash_multiset — klasa kontenera jest rozszerzeniem standardowa biblioteka C++ i jest używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementów zawartych służyć jako wartości klucza i nie muszą być unikatowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>  
class hash_multiset  
```  
  
#### <a name="parameters"></a>Parametry  
 *Key*  
 Typ danych elementu mają być przechowywane w hash_multiset.  
  
 `Traits`  
 Typu, który obejmuje dwa obiekty funkcji, co klasa porównania oznacza to predykat binarnych możliwe do porównania dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względną i funkcji skrótu, która jest jednoargumentowy predykatu mapowania klucza wartości elementów na typy niepodpisane liczby całkowite typu **size_t**. Ten argument jest opcjonalny i `hash_compare` *< klucz,* **mniej ***\<klucza >>* jest wartością domyślną.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji hash_multiset i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to **alokatora ***\<klucza >.*  
  
## <a name="remarks"></a>Uwagi  
 Hash_multiset — jest:  
  
-   Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.  
  
-   Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.  
  
-   Wartość skrótu, ponieważ jej elementy są pogrupowane w pakiety na podstawie wartości funkcji skrótu zastosowane do wartości kluczy elementów.  
  
-   Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_multiset również jest kontenerem asocjacyjnej proste, jego elementów również są unikatowe.  
  
-   Klasa szablonu, ponieważ zawiera funkcje jest ogólnym i dlatego niezależnie od określonego typu danych znajdujących się jako elementy lub kluczy. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.  
  
 Główną zaletą tworzenia skrótów za pośrednictwem sortowanie jest większą wydajność: wykonuje wstawienia, usuwanie i wyszukuje w stałej Średni czas w porównaniu z danej chwili proporcjonalna do logarytmu liczba elementów w kontenerze sortowania pomyślnego tworzenia skrótów techniki. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.  
  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjna skrótu są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje Członkowskie, które jawnie obsługują te operacje są wydajne, gdy jest używany z funkcji skrótu dobrze zaprojektowanego, wykonywanie ich w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego tworzy uniform rozkład wartości skrótu i minimalizuje liczbę konfliktów, gdzie jest określany kolizji występuje, gdy różne wartości klucza są zamapowane na tę samą wartość skrótu. W najgorszym przypadku przy użyciu najgorszy funkcji skrótu to możliwe liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowej).  
  
 Hash_multiset — powinien być asocjacyjnej kontener wyboru podczas kojarzenia wartości z ich kluczy warunki są spełnia przez aplikację. Elementy hash_multiset mogą być wielokrotnością i służyć jako własne klucze sortowania, więc nie są unikatowe klucze. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować więcej niż jeden raz. Ma wiele wystąpień słowa zostały niedozwolone, następnie hash_set byłby struktury odpowiedniego kontenera. Jeśli unikatowy definicje zostały dołączone jako wartości do listy unikatowych słów kluczowych, hash_map będzie odpowiednie struktury zawiera te dane. Jeśli zamiast tego definicje nie były unikatowe, hash_multimap będzie kontener wyboru.  
  
 Hash_multiset — porządkuje sekwencji kontroluje przez wywołanie obiektu skrótu przechowywaną cech typu [value_compare](#value_compare). Ten obiekt przechowywane, mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Obiekt funkcji musi działają tak samo, jak obiekt klasy `hash_compare` *< klucz,* **mniej ***\<klucza >>.* W szczególności dla wszystkich wartości *klucza* typu **klucza**, wywołanie **cechy**( *klucza*) daje rozkład wartości typu **size_t**.  
  
 Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argument x i y i zostać zwrócona wartość PRAWDA lub FAŁSZ. Kolejność na hash_multiset jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty x i y są zdefiniowane jako równoważne, gdy oba *f* ( *x*, *y*) i *f*( *y*, *x*) to wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.  
  
 Rzeczywiste kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcja porządkowania i bieżący rozmiar tablicy skrótów przechowywane w obiekcie kontenera. Nie można ustalić bieżący rozmiar tablicy skrótów, więc nie można przewidzieć ogólnie kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.  
  
 Iterator dostarczonych przez hash_multiset — klasa jest iteratora dwukierunkowego, ale Wstaw funkcje Członkowskie klas i hash_multiset ma wersje, które przyjmować jako parametry szablonu słabszych iteratora wejściowych, którego wymagania funkcji są minimalne więcej niż te gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma własną hash_multiset wymagania i algorytmy, które współpracują z nich należy ograniczyć ich założenia wymagania udostępniane przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multiset funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory [ `first`, `last`) w kontekście funkcji elementów członkowskich klasy.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[hash_multiset —](#hash_multiset)|Konstruuje `hash_multiset` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `hash_multiset`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `hash_multiset` obiektu.|  
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_multiset`.|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element `hash_multiset`.|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w `hash_multiset` do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_multiset`.|  
|[difference_type](#difference_type)|Typ liczbę całkowitą ze znakiem, który zawiera różnicę między dwoma Iteratory, które rozwiązują elementów w tym samym `hash_multiset`.|  
|[iterator](#iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w `hash_multiset`.|  
|[key_compare](#key_compare)|Typ, który zawiera obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multiset`.|  
|[key_type](#key_type)|Typ, który opisuje obiekt zapisany jako elementu `hash_set` jako klucza sortowania.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu `hash_multiset`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `hash_multiset`.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `hash_multiset`.|  
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `hash_multiset`.|  
|[value_compare —](#value_compare)|Typ, który udostępnia dwa obiekty funkcji, binary predykatu porównania klasy, które można porównać dwóch wartości elementu `hash_multiset` ustalenie ich względne kolejności i jednoargumentowy predykat, który tworzy skrót elementów.|  
|[value_type](#value_type)|Typ, który opisuje obiekt zapisany jako elementu `hash_multiset` jako wartość.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[begin](#begin)|Zwraca iteratora, którego dotyczy pierwszym elementem w `hash_multiset`.|  
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w `hash_multiset`.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `hash_multiset`.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_multiset`.|  
|[Liczba](#count)|Zwraca liczbę elementów w `hash_multiset` którego klucz odpowiada klucz określony parametr|  
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszym elementem w odwróconej `hash_multiset`.|  
|[crend](#crend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej `hash_multiset`.|  
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `hash_multiset`.|  
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `hash_multiset`, ze wskazówką umieszczania.|  
|[empty](#empty)|Sprawdza, czy `hash_multiset` jest pusta.|  
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `hash_multiset`.|  
|[equal_range](#equal_range)|Zwraca parę Iteratory odpowiednio do pierwszego elementu w `hash_multiset` za pomocą klucza, który jest większy niż określony klucz i pierwszy element w `hash_multiset` za pomocą klucza jest równa lub większa niż klucz.|  
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `hash_multiset` z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.|  
|[Znajdź](#find)|Zwraca iteratora adresowania położenie elementu w `hash_multiset` mający klucz równoważne z określonym kluczem.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` użyty do utworzenia obiektu `hash_multiset`.|  
|[insert](#insert)|Wstawia element lub zakres elementów do `hash_multiset`.|  
|[key_comp](#key_compare)|Pobiera kopię porównania obiekt używany do kolejność kluczy w `hash_multiset`.|  
|[lower_bound](#lower_bound)|Zwraca pierwszy element w iteratora `hash_multiset` za pomocą klucza, który jest równy lub większy niż określony klucz.|  
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multiset`.|  
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszym elementem w odwróconej `hash_multiset`.|  
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej `hash_multiset`.|  
|[Rozmiar](#size)|Zwraca liczbę elementów w `hash_multiset`.|  
|[swap](#swap)|Zamienia elementy dwóch `hash_multiset`s.|  
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `hash_multiset` który za pomocą klucza, który jest równy lub większy niż określony klucz.|  
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność wartości klucza w elemencie `hash_multiset`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[hash_multiset::operator =](#op_eq)|Zamienia elementy hash_multiset kopię hash_multiset innego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<hash_set >  
  
 **Namespace:** stdext —  
  
##  <a name="allocator_type"></a>  hash_multiset::allocator_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który reprezentuje klasę alokatora dla obiekt hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą `allocator_type`  
  
##  <a name="begin"></a>  hash_multiset::BEGIN  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca, którego dotyczy pierwszym elementem w hash_multiset iteratora.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adresowanie pierwszym elementem w hash_multiset lub lokalizacji pomyślne pusty hash_multiset iteratora dwukierunkowego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować elementów w obiekcie hash_multiset. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iterator**, elementów w obiekcie hash_multiset może być modyfikowany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_begin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::const_iterator hms1_cIter;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
   hms1.insert( 3 );  
  
   hms1_Iter = hms1.begin( );  
   cout << "The first element of hms1 is " << *hms1_Iter << endl;  
  
   hms1_Iter = hms1.begin( );  
   hms1.erase( hms1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hms1_cIter = hms1.begin( );  
   // hms1.erase( hms1_cIter );  
  
   hms1_cIter = hms1.begin( );  
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;  
}  
```  
  
```Output  
The first element of hms1 is 1  
The first element of hms1 is now 2  
```  
  
##  <a name="cbegin"></a>  hash_multiset::cbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca iteratora const, który dotyczy pierwszym elementem w hash_multiset.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego adresowania pierwszym elementem w [hash_multiset](../standard-library/hash-multiset-class.md) lub lokalizacji pomyślne pustą `hash_multiset`.  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w `hash_multiset` obiektu nie może być modyfikowany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_cbegin.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_cIter = hs1.cbegin( );  
   cout << "The first element of hs1 is " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The first element of hs1 is 1  
```  
  
##  <a name="cend"></a>  hash_multiset::cend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w hash_multiset.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w [hash_multiset](../standard-library/hash-multiset-class.md). Jeśli `hash_multiset` jest pusta, następnie `hash_multiset::cend == hash_multiset::begin`.  
  
### <a name="remarks"></a>Uwagi  
 `cend` Służy do sprawdzenia, czy iteratora osiągnął koniec jego `hash_multiset`. Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_cend.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int> :: const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_cIter = hs1.cend( );  
   hs1_cIter--;  
   cout << "The last element of hs1 is " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The last element of hs1 is 3  
```  
  
##  <a name="clear"></a>  hash_multiset::Clear  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Usuwa wszystkie elementy hash_multiset.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_clear.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
  
   cout << "The size of the hash_multiset is initially " << hms1.size( )  
        << "." << endl;  
  
   hms1.clear( );  
   cout << "The size of the hash_multiset after clearing is "   
        << hms1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the hash_multiset is initially 2.  
The size of the hash_multiset after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  hash_multiset::const_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) na przykład za pomocą `const_iterator`.  
  
##  <a name="const_pointer"></a>  hash_multiset::const_pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który dostarcza wskaźnik do **const** element hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [const_iterator](#const_iterator) mają być używane do uzyskania dostępu do elementów w **const** hash_multiset obiektu.  
  
   
  
##  <a name="const_reference"></a>  hash_multiset::const_reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który zawiera odwołanie do **const** element przechowywane w hash_multiset do odczytu i wykonywania **const** operacji.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_const_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *hms1.begin( );  
  
   cout << "The first element in the hash_multiset is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the hash_multiset  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the hash_multiset is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację hash_multiset — odwrotnie.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.  
  
##  <a name="count"></a>  hash_multiset::Count  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca liczbę elementów w hash_multiset, którego klucz odpowiada parametr określony klucz.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz elementu do dopasowania z hash_multiset.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w hash_multiset kluczem określony przez parametr.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów w następującym zakresie:  
  
 [ `lower_bound` (_ `Key` ), `upper_bound` (\_ `Key` ) ).  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multiset::count.  
  
```  
// hash_multiset_count.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multiset<int> hms1;  
    hash_multiset<int>::size_type i;  
  
    hms1.insert(1);  
    hms1.insert(1);  
  
    // Keys do not need to be unique in hash_multiset,  
    // so duplicates may exist.  
    i = hms1.count(1);  
    cout << "The number of elements in hms1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hms1.count(2);  
    cout << "The number of elements in hms1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hms1 with a sort key of 1 is: 2.  
The number of elements in hms1 with a sort key of 2 is: 0.  
```  
  
##  <a name="crbegin"></a>  hash_multiset::crbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca const iteratora adresowania pierwszym elementem w odwróconej hash_multiset.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [hash_multiset](../standard-library/hash-multiset-class.md) lub adresowania co była ostatnim elementem w stałe `hash_multiset`.  
  
### <a name="remarks"></a>Uwagi  
 `crbegin` jest używany z odwróconej `hash_multiset` podobnie jak [hash_multiset::begin](#begin) jest używany z `hash_multiset`.  
  
 Z wartością zwracaną z `crbegin`, `hash_multiset` obiektu nie może być modyfikowany.  
  
 `crbegin` może służyć do iterowania po `hash_multiset` Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_crbegin.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crbegin( );  
   cout << "The first element in the reversed hash_multiset is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_multiset is 30.  
```  
  
##  <a name="crend"></a>  hash_multiset::crend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multiset.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [hash_multiset](../standard-library/hash-multiset-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `hash_multiset`).  
  
### <a name="remarks"></a>Uwagi  
 `crend` jest używany z odwróconej `hash_multiset` podobnie jak [hash_multiset::end](#end) jest używany z `hash_multiset`.  
  
 Z wartością zwracaną z `crend`, `hash_multiset` obiektu nie może być modyfikowany.  
  
 `crend` można sprawdzać, czy osiągnął koniec jego hash_multiset odwrotnej iteratora.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_crend.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crend( );  
   hs1_crIter--;  
   cout << "The last element in the reversed hash_multiset is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_multiset is 10.  
```  
  
##  <a name="difference_type"></a>  hash_multiset::difference_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ liczbę całkowitą ze znakiem, który udostępnia różnica między dwa Iteratory, które rozwiązują elementów w obrębie tego samego hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakres elementów do , ale bez tego elementu wskazywanego przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez odwracalnego kontenerów, takiego jak zestaw. Odejmowanie między Iteratory jest obsługiwana tylko przez Iteratory dostępie swobodnym udostępniane przez kontener dostępie swobodnym, takich jak wektorowa lub deque —.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;  
  
   hms1.insert( 20 );  
   hms1.insert( 10 );  
  
   // hash_multiset elements need not be unique  
   hms1.insert( 20 );  
  
   hms1_bIter = hms1.begin( );  
   hms1_eIter = hms1.end( );  
  
   hash_multiset <int>::difference_type   df_typ5, df_typ10,  
        df_typ20;  
  
   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );  
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );  
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );  
  
   // The keys & hence the elements of a hash_multiset  
   // need not be unique and may occur multiple times  
   cout << "The number '5' occurs " << df_typ5  
        << " times in hash_multiset hms1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in hash_multiset hms1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in hash_multiset hms1.\n";  
  
   // Count the number of elements in a hash_multiset  
   hash_multiset <int>::difference_type  df_count = 0;  
   hms1_Iter = hms1.begin( );  
   while ( hms1_Iter != hms1_eIter)  
   {  
      df_count++;  
      hms1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_multiset hms1 is "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in hash_multiset hms1.  
The number '10' occurs 1 times in hash_multiset hms1.  
The number '20' occurs 2 times in hash_multiset hms1.  
The number of elements in the hash_multiset hms1 is 3.  
```  
  
##  <a name="emplace"></a>  hash_multiset::emplace  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Wstawia element utworzyć spełnione hash_multiset.  
  
```  
template <class ValTy>  
iterator insert(ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Wartość elementu ma zostać wstawiony do [hash_multiset](../standard-library/hash-multiset-class.md) chyba że `hash_multiset` zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `emplace` Funkcją członkowską zwracającą iterator wskazujący miejsce, w którym dodano nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_emplace.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<string> hms3;  
   string str1("a");  
  
   hms3.emplace(move(str1));  
   cout << "After the emplace insertion, hms3 contains "  
      << *hms3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hms3 contains a.  
```  
  
##  <a name="emplace_hint"></a>  hash_multiset::emplace_hint  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Wstawia element utworzyć spełnione hash_multiset, ze wskazówką umieszczania.  
  
```  
template <class ValTy>  
iterator insert(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Wartość elementu ma zostać wstawiony do [hash_multiset](../standard-library/hash-multiset-class.md) chyba że `hash_multiset` zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
|`_Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.)|  
  
### <a name="return-value"></a>Wartość zwracana  
 [Hash_multiset::emplace](#emplace) funkcją członkowską zwracającą iterator wskazującą położenie, w którym wstawiono nowy element do `hash_multiset`.  
  
### <a name="remarks"></a>Uwagi  
 Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_emplace_hint.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<string> hms1;  
   string str1("a");  
  
   hms1.insert(hms1.begin(), move(str1));  
   cout << "After the emplace insertion, hms1 contains "  
      << *hms1.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hms1 contains a.  
```  
  
##  <a name="empty"></a>  hash_multiset::Empty  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Testy, jeśli hash_multiset jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli hash_multiset jest pusta. **false** Jeśli hash_multiset nie jest pusty.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_empty.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1, hms2;  
   hms1.insert ( 1 );  
  
   if ( hms1.empty( ) )  
      cout << "The hash_multiset hms1 is empty." << endl;  
   else  
      cout << "The hash_multiset hms1 is not empty." << endl;  
  
   if ( hms2.empty( ) )  
      cout << "The hash_multiset hms2 is empty." << endl;  
   else  
      cout << "The hash_multiset hms2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_multiset hms1 is not empty.  
The hash_multiset hms2 is empty.  
```  
  
##  <a name="end"></a>  hash_multiset::end  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_multiset iteratora.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_multiset. Jeśli hash_multiset jest pusty, a następnie hash_multiset::end == hash_multiset::begin.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnął koniec jego hash_multiset. Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_end.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: iterator hms1_Iter;  
   hash_multiset <int> :: const_iterator hms1_cIter;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
   hms1.insert( 3 );  
  
   hms1_Iter = hms1.end( );  
   hms1_Iter--;  
   cout << "The last element of hms1 is " << *hms1_Iter << endl;  
  
   hms1.erase( hms1_Iter );  
  
   // The following 3 lines would err because the iterator is const  
   // hms1_cIter = hms1.end( );  
   // hms1_cIter--;  
   // hms1.erase( hms1_cIter );  
  
   hms1_cIter = hms1.end( );  
   hms1_cIter--;  
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;  
}  
```  
  
```Output  
The last element of hms1 is 3  
The last element of hms1 is now 2  
```  
  
##  <a name="equal_range"></a>  hash_multiset::equal_range  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca parę Iteratory odpowiednio do pierwszego elementu w hash_multiset za pomocą klucza, który jest większy niż określony klucz i pierwszy element w hash_multiset za pomocą klucza jest równa lub większa niż klucz.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multiset przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para Iteratory, w których pierwsza to [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.  
  
 Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi** i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_equal_range.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_multiset<int> IntHSet;  
   IntHSet hms1;  
   hash_multiset <int> :: const_iterator hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;  
   p1 = hms1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20\nin the hash_multiset hms1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20\nin the hash_multiset hms1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   hms1_RcIter = hms1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *hms1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = hms1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hms1.end( ) )   
      && ( p2.second == hms1.end( ) ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1"  
           << "with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20  
in the hash_multiset hms1 is: 30.  
The lower bound of the element with a key of 20  
in the hash_multiset hms1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The hash_multiset hms1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  hash_multiset::ERASE  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Usuwa element lub zakres elementów w hash_multiset z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Położenie elementu do usunięcia z hash_multiset.  
  
 `first`  
 Pozycja pierwszego elementu usunięte z hash_multiset.  
  
 `last`  
 Pozycja poza ostatni element usunięty z hash_multiset.  
  
 `key`  
 Klucz elementów do usunięcia z hash_multiset.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostała poza wszelkie elementy usunięte lub wskaźnika do końca hash_multiset nie zawiera żadnego takiego elementu. Trzeci funkcji Członkowskich, liczba elementów, które zostały usunięte z hash_multiset.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie nigdy nie zgłaszają wyjątków.  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multiset::erase.  
  
```  
// hash_multiset_erase.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multiset<int> hms1, hms2, hms3;  
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_multiset<int>::size_type n;  
  
    for (i = 1; i < 5; i++)  
    {  
        hms1.insert(i);  
        hms2.insert(i * i);  
        hms3.insert(i - 1);  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hms1.begin();  
    hms1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted,\n "  
         << "the hash_multiset hms1 is:" ;  
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hms2.begin();  
    Iter2 = --hms2.end();  
    hms2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted,\n "  
         << "the hash_multiset hms2 is:" ;  
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hms3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n "  
         << "the hash_multiset hms3 is:" ;  
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hms3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hms3.begin();  
    hms3.erase(Iter1);  
  
    cout << "After another element with a key "  
         << "equal to that of the 2nd element\n is deleted, "  
         << "the hash_multiset hms3 is:" ;  
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted,  
 the hash_multiset hms1 is: 1 3 4.  
After the middle two elements are deleted,  
 the hash_multiset hms2 is: 16 4.  
After the element with a key of 2 is deleted,  
 the hash_multiset hms3 is: 0 1 3.  
The number of elements removed from hms3 is: 1.  
After another element with a key equal to that of the 2nd element  
 is deleted, the hash_multiset hms3 is: 0 3.  
```  
  
##  <a name="find"></a>  hash_multiset::Find  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca iteratora adresowania położenie elementu w hash_multiset, który ma klucz równoważne z określonym kluczem.  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu wartością klucza sortowania z elementem z hash_multiset przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Iterator](#iterator) lub [const_iterator](#const_iterator) który adresy lokalizacji elementu równoważne z określonym kluczem lub który adresów lokalizacji pomyślne ostatnim elementem w hash_multiset, jeśli jest niezgodna Znaleziono dla klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcją członkowską zwracającą iterator, którego dotyczy element hash_multiset, którego klucz sortowania jest **równoważne** do argumentu klucz w obszarze binarny predykatu wywołujące kolejność oparty na mniej-niż porównywalności relacji.  
  
 Jeśli wartość zwracana **znaleźć** jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, można zmodyfikować obiektu hash_multiset.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_find.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.find( 20 );  
   cout << "The element of hash_multiset hms1 with a key of 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.find( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1 with a key of 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // The element at a specific location in the hash_multiset can be found   
   // by using a dereferenced iterator addressing the location  
   hms1_AcIter = hms1.end( );  
   hms1_AcIter--;  
   hms1_RcIter = hms1.find( *hms1_AcIter );  
   cout << "The element of hms1 with a key matching "  
        << "that of the last element is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_multiset hms1 with a key of 20 is: 20.  
The hash_multiset hms1 doesn't have an element with a key of 40.  
The element of hms1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>  hash_multiset::get_allocator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca kopię obiektu alokatora użyta do skonstruowania hash_multiset.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Program przydzielania służy do zarządzania pamięci, która jest parametr szablonu klasy hash_multiset `Allocator`.  
  
 Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy hash_multiset Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_multiset <int, hash_compare <int, less<int> > > hms1;  
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;  
   hash_multiset <double, hash_compare <double,  
      less<double> >, allocator<double> > hms3;  
  
   hash_multiset <int, hash_compare <int,  
      greater<int> > >::allocator_type hms2_Alloc;  
   hash_multiset <double>::allocator_type hms3_Alloc;  
   hms2_Alloc = hms2.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hms1.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hms3.max_size( ) <<  "." << endl;  
  
   // The following lines create a hash_multiset hms4  
   // with the allocator of hash_multiset hms1.  
   hash_multiset <int>::allocator_type hms4_Alloc;  
   hash_multiset <int> hms4;  
   hms4_Alloc = hms2.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hms2_Alloc == hms4_Alloc )  
   {  
      cout << "The allocators are interchangeable."  
           << endl;  
   }  
   else  
   {  
      cout << "The allocators are not interchangeable."  
           << endl;  
   }  
}  
```  
  
##  <a name="hash_multiset"></a>  hash_multiset::hash_multiset  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Konstruuje `hash_multiset` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `hash_multiset`.  
  
```  
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,  
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right  
};  
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):  
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa przydzielania magazynu do użycia dla tego `hash_multiset` obiektu, który domyślnie `Allocator`.|  
|`Comp`|Funkcja porównywania typu `const Traits` porządkowania elementów w `hash_multiset`, jakie nie `hash_compare`.|  
|`Right`|`hash_multiset` Którego zbudowany `hash_multiset` ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Initializer_list, który zawiera elementy do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory przechowywania typu obiektu przydzielania, który zarządza przechowywania w pamięci dla `hash_multiset` i który później może być zwracany przez wywołanie metody [hash_multiset::get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.  
  
 Wszystkie konstruktory zainicjować ich hash_multisets.  
  
 Wszystkie konstruktory przechowywania obiektem funkcji typu `Traits` używany do ustanawiania kolejność kluczy `hash_multiset` i który później może być zwracany przez wywołanie metody [hash_multiset::key_comp](#key_comp). Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
 Pierwsze trzy konstruktorów Określ pusty początkowego `hash_multiset`, drugi określający typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów i trzeci jawnie określając programu przydzielania wpisz ( `Al`) do użycia. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.  
  
 Przenosi czwarty konstruktora `hash_multiset` `Right`.  
  
 Piąty szóstego i siódmy initializer_list użyj konstruktorów.  
  
 Ostatnie trzy konstruktorów skopiuj zakres [ `First`, `Last`) z `hash_multiset` rosnącymi explicitness określania typu porównanie funkcji klasy porównania i przydzielania.  
  
 Rzeczywiste kolejność elementów w kontenerze skrótem zestawu zależy od funkcji skrótu, funkcja porządkowania i bieżący rozmiar tablicy skrótów i ogólnie rzecz biorąc, nie można przewidzieć, ponieważ może to z kontenerem zestawu, w której była określana przez funkcję porządkowania samodzielnie.  
  
##  <a name="insert"></a>  hash_multiset::INSERT  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Wstawia element lub zakres elementów do hash_multiset.  
  
```  
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,  
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,   
    const Type& Val);

template <class InputIterator>  
void insert(
    InputIterator First,  
    InputIterator Last);

template <class ValTy>  
iterator insert(
    ValTy&& Val);

template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Val`|Wartość elementu ma zostać wstawiony do hash_multiset, chyba że hash_multiset zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.)|  
|`First`|Pozycja pierwszego elementu skopiowane z hash_multiset.|  
|`Last`|Pozycja poza ostatni element do skopiowania z hash_multiset.|  
|`IList`|Initializer_list, który zawiera elementy, aby skopiować.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji Członkowskich Wstaw dwa zwracać iterację, który wskazuje miejsce, w którym dodano nowego elementu.  
  
 Funkcje Członkowskie trzech kolejnych używają initializer_list.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji wartości elementów do hash_multiset odpowiadający każdemu elementowi adresowane przez iterator w zakresie [ `First`, `Last`) z określonym hash_multiset.  
  
### <a name="remarks"></a>Uwagi  
 Wstawiania może wystąpić w amortyzowanego stałej czasu dla wersji wskazówka insert, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `Where`.  
  
##  <a name="iterator"></a>  hash_multiset::iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **iterator** może służyć do modyfikowania wartości elementu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_comp"></a>  hash_multiset::key_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Pobiera kopię porównania obiekt używany do kolejność kluczy w hash_multiset.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca parametr szablonu hash_multiset `Traits`, który zawiera obiekty funkcji, które są używane do wyznaczania wartości skrótu oraz do porządkowania elementów kontenera.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **const klucza &** *_xVal,* **const klucza &** _ `yVal`);  
  
 która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla klasy hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdzie są unikatowe i hash_multiset.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_key_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int, hash_compare < int, less<int> > >hms1;  
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1  
          = hms1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of hms1."  
           << endl;  
   }  
   else  
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of hms1."  
        << endl;  
   }  
  
   hash_multiset <int, hash_compare < int, greater<int> > > hms2;  
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare  
         kc2 = hms2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of hms2."  
           << endl;  
   }  
   else  
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of hms2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>  hash_multiset::key_compare  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ zawiera dwa obiekty funkcji, binary predykatu porównania klasy, które można porównać dwóch wartości elementu hash_multiset, aby określić ich kolejność względną i predykat jednoargumentowe, który tworzy skrót elementy.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 **key_compare** jest synonimem parametru szablonu `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
 Należy pamiętać, że oba `key_compare` i value_compare są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla klasy hash_set i hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="key_type"></a>  hash_multiset::key_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który udostępnia obiekt funkcji, które można porównać klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multiset.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 **key_type** jest synonimem parametru szablonu `Key`.  
  
 Należy pamiętać, że oba `key_type` i [value_type](../standard-library/hash-set-class.md#value_type) są synonimy dla parametru szablonu **klucza**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.  
  
 Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.  
  
##  <a name="lower_bound"></a>  hash_multiset::lower_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca pierwszy element w hash_multiset iteratora klucz, który jest równy lub większy niż określony klucz.  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multiset przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Iterator](#iterator) lub [const_iterator](#const_iterator) który dotyczy położenie pierwszego elementu w hash_multiset za pomocą klucza jest równa lub większa niż klucz argumentu lub który dotyczy pomyślne lokalizacji ostatni element hash_multiset, jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.lower_bound( 20 );  
   cout << "The element of hash_multiset hms1 with a key of 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1 with a key of 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_multiset can be found   
   // by using a dereferenced iterator that addresses the location  
   hms1_AcIter = hms1.end( );  
   hms1_AcIter--;  
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );  
   cout << "The element of hms1 with a key matching "  
        << "that of the last element is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
##  <a name="max_size"></a>  hash_multiset::max_size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca maksymalną długość hash_multiset.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe hash_multiset.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_max_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::size_type i;  
  
   i = hms1.max_size( );     
   cout << "The maximum possible length "  
        << "of the hash_multiset is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq">hash_multiset::operator =</a>  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zamienia elementy hash_multiset kopię hash_multiset innego.  
  
```  
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Hash_multiset](../standard-library/hash-multiset-class.md) kopiowane do `hash_multiset`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `hash_multiset`, `operator=` albo kopiuje lub przenosi zawartość `right` do `hash_multiset`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_operator_as.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<int> v1, v2, v3;  
   hash_multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="pointer"></a>  hash_multiset::Pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który dostarcza wskaźnik do elementu hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów zestawów wielokrotnych obiektu.  
  
   
  
##  <a name="rbegin"></a>  hash_multiset::rbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca iteratora adresowania pierwszym elementem w hash_multiset odwróconej.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego adresowania pierwszym elementem w odwróconej hash_multiset lub adresowania co była ostatnim elementem w hash_multiset stałe.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z odwróconej hash_multiset — podobnie jak [rozpocząć](#begin) jest używany z hash_multiset.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, a następnie nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu hash_multiset.  
  
 `rbegin` może służyć do iterowania po hash_multiset Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_rbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::reverse_iterator hms1_rIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_rIter = hms1.rbegin( );  
   cout << "The first element in the reversed hash_multiset is "  
        << *hms1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a hash_multiset in a forward order  
   cout << "The hash_multiset is: ";  
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
      cout << *hms1_Iter << " ";  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a hash_multiset in a reverse order  
   cout << "The reversed hash_multiset is: ";  
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );  
         hms1_rIter++ )  
      cout << *hms1_rIter << " ";  
   cout << endl;  
  
   // A hash_multiset element can be erased by dereferencing to its key   
   hms1_rIter = hms1.rbegin( );  
   hms1.erase ( *hms1_rIter );  
  
   hms1_rIter = hms1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_multiset is 30.  
The hash_multiset is: 10 20 30   
The reversed hash_multiset is: 30 20 10   
After the erasure, the first element in the reversed hash_multiset is 20.  
```  
  
##  <a name="reference"></a>  hash_multiset::Reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który zawiera odwołanie do elementu przechowywane w hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   int &Ref1 = *hms1.begin( );  
  
   cout << "The first element in the hash_multiset is "  
        << Ref1 << "." << endl;  
  
   // The value of the 1st element of the hash_multiset can be  
   // changed by operating on its (non const) reference  
   Ref1 = Ref1 + 5;  
  
   cout << "The first element in the hash_multiset is now "  
        << *hms1.begin() << "." << endl;  
}  
```  
  
```Output  
The first element in the hash_multiset is 10.  
The first element in the hash_multiset is now 15.  
```  
  
##  <a name="rend"></a>  hash_multiset::rend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multiset iteratora.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multiset (lokalizacja miał przed pierwszym elementem w stałe hash_multiset).  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z odwróconej hash_multiset — podobnie jak [zakończenia](#end) jest używany z hash_multiset.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, a następnie nie można zmodyfikować obiektu hash_multiset. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu hash_multiset. Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
 `rend` można sprawdzać, czy osiągnął koniec jego hash_multiset odwrotnej iteratora.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_rend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::reverse_iterator hms1_rIter;  
   hash_multiset <int>::const_reverse_iterator hms1_crIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   cout << "The last element in the reversed hash_multiset is "  
        << *hms1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // through a hash_multiset in a forward order  
   cout << "The hash_multiset is: ";  
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
      cout << *hms1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // throught a hash_multiset in a reverse order  
   cout << "The reversed hash_multiset is: ";  
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );  
         hms1_rIter++ )  
      cout << *hms1_rIter << " ";  
   cout << "." << endl;  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   hms1.erase ( *hms1_rIter );  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   cout << "After the erasure, the last element in the "  
        << "reversed hash_multiset is " << *hms1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_multiset is 10.  
The hash_multiset is: 10 20 30 .  
The reversed hash_multiset is: 30 20 10 .  
After the erasure, the last element in the reversed hash_multiset is 20.  
```  
  
##  <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który zapewnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować element hash_multiset odwróconej.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` umożliwia iterację hash_multiset — odwrotnie.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="size"></a>  hash_multiset::size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca liczbę elementów w hash_multiset.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość hash_multiset.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: size_type i;  
  
   hms1.insert( 1 );  
   i = hms1.size( );  
   cout << "The hash_multiset length is " << i << "." << endl;  
  
   hms1.insert( 2 );  
   i = hms1.size( );  
   cout << "The hash_multiset length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_multiset length is 1.  
The hash_multiset length is now 2.  
```  
  
##  <a name="size_type"></a>  hash_multiset::size_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`  
  
##  <a name="swap"></a>  hash_multiset::swap  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zamienia hash_multisets dwa elementy.  
  
```  
void swap(hash_multiset& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_multiset — argument, zapewniając elementy, aby być zamieniona na hash_multiset docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch hash_multisets, której elementy są wymieniane.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_swap.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1, hms2, hms3;  
   hash_multiset <int>::iterator hms1_Iter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
   hms2.insert( 100 );  
   hms2.insert( 200 );  
   hms3.insert( 300 );  
  
   cout << "The original hash_multiset hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hms1.swap( hms2 );  
  
   cout << "After swapping with hms2, list hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hms1, hms3 );  
  
   cout << "After swapping with hms3, list hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_multiset hms1 is: 10 20 30.  
After swapping with hms2, list hms1 is: 200 100.  
After swapping with hms3, list hms1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  hash_multiset::upper_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Zwraca pierwszy element w hash_multiset iteratora klucz, który jest większy niż określony klucz.  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multiset przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Iterator](#iterator) lub [const_iterator](#const_iterator) który dotyczy położenie pierwszego elementu w hash_multiset za pomocą klucza większe klucz argumentu, lub które adresów pomyślne ostatnim elementem w lokalizacji hash_multiset — Jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.upper_bound( 20 );  
   cout << "The first element of hash_multiset hms1" << endl  
        << " with a key greater than 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "\n with a key greater than 30." << endl;  
   else  
      cout << "The element of hash_multiset hms1"  
           << "with a key > 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_multiset can be  
   // found by using a dereferenced iterator addressing the location  
   hms1_AcIter = hms1.begin( );  
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );  
   cout << "The first element of hms1\n with a key greater than "  
        << endl << "that of the initial element of hms1 is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of hash_multiset hms1  
 with a key greater than 20 is: 30.  
The hash_multiset hms1 doesn't have an element   
 with a key greater than 30.  
The first element of hms1  
 with a key greater than   
that of the initial element of hms1 is: 20.  
```  
  
##  <a name="value_comp"></a>  hash_multiset::value_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Pobiera kopię porównania obiekt używany do wartości elementu kolejności w hash_multiset.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca parametr szablonu hash_multiset `Traits`, który zawiera obiekty funkcji, które są używane do wyznaczania wartości skrótu i kolejność elementów kontenera.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **constKey &**`_xVal`, **const klucza &** *_yVal*);  
  
 która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla klasy hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdzie są unikatowe i hash_multiset.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_value_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int, hash_compare < int, less<int> > > hms1;  
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare  
      vc1 = hms1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )  
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of hms1."  
           << endl;  
   }  
   else  
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of hms1."  
           << endl;  
   }  
  
   hash_multiset <int, hash_compare < int, greater<int> > > hms2;  
   hash_multiset<int, hash_compare < int, greater<int> > >::  
           value_compare vc2 = hms2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )  
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of hms2."  
           << endl;  
   }  
   else  
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of hms2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.  
```  
  
##  <a name="value_compare"></a>  hash_multiset::value_compare  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ zawiera dwa obiekty funkcji, binary predykatu porównania klasy, które można porównać dwóch wartości elementu hash_multiset, aby określić ich kolejność względną i predykat jednoargumentowe, który tworzy skrót elementy.  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 **value_compare** jest synonimem parametru szablonu `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multiset — klasa](../standard-library/hash-multiset-class.md) tematu.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i **value_compare** są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu klas i zestaw wielokrotny, gdzie są one identyczne, aby zapewnić zgodność z mapowania klas i multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_comp](#value_comp) przykład sposobu deklarowanie i użycie `value_compare`.  
  
##  <a name="value_type"></a>  hash_multiset::value_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).  
  
 Typ, który opisuje obiekt zapisany jako elementu jako hash_multiset jako wartość.  
  
```  
typedef Key value_type;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multiset_value_type.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
  
   // Declare value_type  
   hash_multiset <int> :: value_type hmsvt_Int;   
  
   hmsvt_Int = 10;   // Initialize value_type  
  
   // Declare key_type  
   hash_multiset <int> :: key_type hmskt_Int;  
   hmskt_Int = 20;             // Initialize key_type  
  
   hms1.insert( hmsvt_Int );         // Insert value into s1  
   hms1.insert( hmskt_Int );         // Insert key into s1  
  
   // A hash_multiset accepts key_types or value_types as elements  
   cout << "The hash_multiset has elements:";  
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );  
         hms1_Iter++)  
      cout << " " << *hms1_Iter;  
      cout << "." << endl;  
}  
```  
  
```Output  
The hash_multiset has elements: 10 20.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

