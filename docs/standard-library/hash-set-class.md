---
title: "hash_set — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
dev_langs: C++
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dd9f781b39db5e8c9df5e70a4a291db44e61cbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hashset-class"></a>hash_set — Klasa
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Hash_set — klasa kontenera jest rozszerzeniem standardowa biblioteka C++ i jest używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key,   
    class Traits=hash_compare<Key, less<Key>>,   
    class Allocator=allocator<Key>>  
class hash_set  
```  
  
#### <a name="parameters"></a>Parametry  
 `Key`  
 Typ danych elementu mają być przechowywane w hash_set.  
  
 `Traits`  
 Typu, który obejmuje dwa obiekty funkcji, co klasa porównania oznacza to predykat binarnych możliwe do porównania dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względną i funkcji skrótu, która jest jednoargumentowy predykatu mapowania klucza wartości elementów na typy niepodpisane liczby całkowite typu **size_t**. Ten argument jest opcjonalny i `hash_compare` *< klucz,* **mniej***\<klucza >>* jest wartością domyślną.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji hash_set i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to **alokatora***\<klucza >.*  
  
## <a name="remarks"></a>Uwagi  
 Hash_set — jest:  
  
-   Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.  
  
-   Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.  
  
-   Wartość skrótu, ponieważ jej elementy są pogrupowane w pakiety na podstawie wartości funkcji skrótu zastosowane do wartości kluczy elementów.  
  
-   Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ hash_set również jest kontenerem asocjacyjnej proste, jego elementów również są unikatowe.  
  
-   Klasa szablonu, ponieważ zawiera funkcje jest ogólnym i dlatego niezależnie od określonego typu danych znajdujących się jako elementy lub kluczy. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.  
  
 Główną zaletą tworzenia skrótów za pośrednictwem sortowanie jest większą wydajność; wykonuje wstawienia, usuwanie i wyszukuje w stałej Średni czas w porównaniu z danej chwili proporcjonalna do logarytmu liczba elementów w kontenerze sortowania techniki pomyślnego tworzenia skrótów. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.  
  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjna skrótu są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje Członkowskie, które jawnie obsługują te operacje są wydajne, gdy jest używany z funkcji skrótu dobrze zaprojektowanego, wykonywanie ich w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego tworzy uniform rozkład wartości skrótu i minimalizuje liczbę konfliktów, gdzie jest określany kolizji występuje, gdy różne wartości klucza są zamapowane na tę samą wartość skrótu. W najgorszym przypadku przy użyciu najgorszy funkcji skrótu to możliwe liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowej).  
  
 Hash_set — powinien być asocjacyjnej kontener wyboru po spełnieniu warunków kojarzenie wartości z ich kluczy przez aplikację. Elementy hash_set są unikatowe i służyć jako własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. W przypadku wielu wystąpień słowa były dozwolone, hash_multiset byłoby struktury odpowiedniego kontenera. Jeśli wartości muszą być dołączone do listy unikatowych słów kluczowych, hash_map będzie odpowiednie struktury zawiera te dane. Jeśli zamiast tego w kluczach nie jest unikatowy, hash_multimap będzie kontener wyboru.  
  
 Hash_set porządkuje sekwencji kontroluje wywołując skrótu przechowywaną **cech** typu obiektu [value_compare](#value_compare). Ten obiekt przechowywane, mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Obiekt funkcji musi działają tak samo, jak obiekt klasy *hash_compare — < klucza mniej\<klucza >>.* W szczególności dla wszystkich wartości `key` typu klucza, wywołanie cechy ( `key` ) daje dystrybucji wartości typu size_t.  
  
 Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to kolejność między elementami odpowiednika. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne *f*( *x*, *y*) jest obiektem funkcji, która ma dwa obiekty argument x i y i zostać zwrócona wartość PRAWDA lub FAŁSZ. Kolejność na hash_set jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty *x* i *y* są zdefiniowane jako równoważne, gdy oba *f*( *x*, *y*) i *f*( *y*, *x*) to wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.  
  
 Rzeczywiste kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcja porządkowania i bieżący rozmiar tablicy skrótów przechowywane w obiekcie kontenera. Nie można ustalić bieżący rozmiar tablicy skrótów, więc nie można przewidzieć ogólnie kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.  
  
 Iteratora podał hash_set — klasa jest iteratora dwukierunkowego, ale funkcje Członkowskie klas [Wstaw](#insert) i [hash_set](#hash_set) wersje przyjmować jako parametry szablonu słabszych iteratora wejściowych, wymagania funkcji, których są bardziej minimalne niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory [ `first`, `last`) w kontekście funkcji elementów członkowskich klasy.  
  
   
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[hash_set —](#hash_set)|Konstruuje `hash_set` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `hash_set`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `hash_set` obiektu.|  
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_set`.|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element `hash_set`.|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w `hash_set` do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_set`.|  
|[difference_type](#difference_type)|Wpisz liczbę całkowitą ze znakiem, służący do reprezentowania liczbę elementów `hash_set` w zakresie między elementami wskazywana przez Iteratory.|  
|[iteratora](#iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w `hash_set`.|  
|[key_compare](#key_compare)|Typ, który zawiera obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_set`.|  
|[key_type](#key_type)|Typ, który opisuje obiekt zapisany jako elementu `hash_set` jako klucza sortowania.|  
|[wskaźnik](#pointer)|Typ, który dostarcza wskaźnik do elementu `hash_set`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `hash_set`.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `hash_set`.|  
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `hash_set`.|  
|[value_compare —](#value_compare)|Typ, który udostępnia dwa obiekty funkcji, binary predykatu porównania klasy, które można porównać dwóch wartości elementu `hash_set` ustalenie ich względne kolejności i jednoargumentowy predykat, który tworzy skrót elementów.|  
|[value_type](#value_type)|Typ, który opisuje obiekt zapisany jako elementu `hash_set` jako wartość.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Rozpocznij](#begin)|Zwraca iteratora, którego dotyczy pierwszym elementem w `hash_set`.|  
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w `hash_set`.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `hash_set`.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_set`.|  
|[Liczba](#count)|Zwraca liczbę elementów w `hash_set` którego klucz odpowiada parametr określony klucz.|  
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszym elementem w odwróconej `hash_set`.|  
|[crend](#crend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej `hash_set`.|  
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `hash_set`.|  
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `hash_set`, ze wskazówką umieszczania.|  
|[pusty](#empty)|Sprawdza, czy `hash_set` jest pusta.|  
|[koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `hash_set`.|  
|[equal_range](#equal_range)|Zwraca parę Iteratory odpowiednio do pierwszego elementu w `hash_set` za pomocą klucza, który jest większy niż określony klucz i pierwszy element w `hash_set` za pomocą klucza jest równa lub większa niż klucz.|  
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `hash_set` z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.|  
|[Znajdź](#find)|Zwraca iteratora adresowania położenie elementu w `hash_set` mający klucz równoważne z określonym kluczem.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` użyty do utworzenia obiektu `hash_set`.|  
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `hash_set`.|  
|[key_comp](#key_comp)|Pobiera kopię porównania obiekt używany do kolejność kluczy w `hash_set`.|  
|[lower_bound —](#lower_bound)|Zwraca pierwszy element w iteratora `hash_set` za pomocą klucza, który jest równy lub większy niż określony klucz.|  
|[max_size](#max_size)|Zwraca maksymalną długość `hash_set`.|  
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszym elementem w odwróconej `hash_set`.|  
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej `hash_set`.|  
|[rozmiar](#size)|Zwraca liczbę elementów w `hash_set`.|  
|[swap](#swap)|Zamienia elementy dwóch `hash_set`s.|  
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `hash_set` który za pomocą klucza, który jest równy lub większy niż określony klucz.|  
|[value_comp](#value_comp)|Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność wartości klucza w elemencie `hash_set`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[hash_set::operator =](#op_eq)|Zastępuje elementy `hash_set` z kopią innego `hash_set`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<hash_set >  
  
 **Namespace:** stdext —  
  
##  <a name="allocator_type"></a>hash_set::allocator_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który reprezentuje klasę alokatora dla obiekt hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 **allocator_type** jest synonimem parametru szablonu `Allocator`.  
  
 Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator) na przykład, który używa `allocator_type`.  
  
##  <a name="begin"></a>hash_set::BEGIN  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca, którego dotyczy pierwszym elementem w hash_set iteratora.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adresowanie pierwszym elementem w hash_set lub lokalizacji pomyślne pusty hash_set iteratora dwukierunkowego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować elementów w obiekcie hash_set. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iterator**, elementów w obiekcie hash_set może być modyfikowany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_begin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_Iter = hs1.begin( );  
   cout << "The first element of hs1 is " << *hs1_Iter << endl;  
  
   hs1_Iter = hs1.begin( );  
   hs1.erase( hs1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hs1_cIter = hs1.begin( );  
   // hs1.erase( hs1_cIter );  
  
   hs1_cIter = hs1.begin( );  
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The first element of hs1 is 1  
The first element of hs1 is now 2  
```  
  
##  <a name="cbegin"></a>hash_set::cbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora const, który dotyczy pierwszym elementem w hash_set.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego adresowania pierwszym elementem w [hash_set](../standard-library/hash-set-class.md) lub lokalizacji pomyślne pustą `hash_set`.  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w `hash_set` obiektu nie może być modyfikowany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_cbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_iterator hs1_cIter;  
  
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
  
##  <a name="cend"></a>hash_set::cend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w hash_set —.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w [hash_set](../standard-library/hash-set-class.md). Jeśli `hash_set` jest pusta, następnie `hash_set::cend == hash_set::begin`.  
  
### <a name="remarks"></a>Uwagi  
 `cend`Służy do sprawdzenia, czy iteratora osiągnął koniec jego `hash_set`. Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_cend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_cIter;  
  
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
  
##  <a name="clear"></a>hash_set::Clear  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Usuwa wszystkie elementy hash_set.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_clear.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
  
   cout << "The size of the hash_set is initially " << hs1.size( )  
        << "." << endl;  
  
   hs1.clear( );  
   cout << "The size of the hash_set after clearing is "   
        << hs1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the hash_set is initially 2.  
The size of the hash_set after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>hash_set::const_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) na przykład, który używa `const_iterator`.  
  
##  <a name="const_pointer"></a>hash_set::const_pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który dostarcza wskaźnik do **const** element hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [const_iterator](#const_iterator) mają być używane do uzyskania dostępu do elementów w **const** hash_set obiektu.  
  
   
  
##  <a name="const_reference"></a>hash_set::const_reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który zawiera odwołanie do **const** element przechowywane w hash_set do odczytu i wykonywania **const** operacji.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_const_ref.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *hs1.begin( );  
  
   cout << "The first element in the hash_set is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the hash_set  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the hash_set is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>hash_set::const_reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację hash_set — odwrotnie.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie`const_reverse_iterator`  
  
##  <a name="count"></a>hash_set::Count  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca liczbę elementów w hash_set, którego klucz odpowiada parametr określony klucz.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz elementu do dopasowania z hash_set.  
  
### <a name="return-value"></a>Wartość zwracana  
 1, jeśli hash_set zawiera element, którego klucz sortowania pasuje do parametru klucza.  
  
 0, jeśli hash_set nie zawiera element z odpowiedniego klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów w następującym zakresie:  
  
 [ **lower_bound** (_ *klucza* ), **upper_bound** (\_ *klucza* )).  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_set::count.  
  
```  
// hash_set_count.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_set<int> hs1;  
    hash_set<int>::size_type i;  
  
    hs1.insert(1);  
    hs1.insert(1);  
  
    // Keys must be unique in hash_set, so duplicates are ignored.  
    i = hs1.count(1);  
    cout << "The number of elements in hs1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hs1.count(2);  
    cout << "The number of elements in hs1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hs1 with a sort key of 1 is: 1.  
The number of elements in hs1 with a sort key of 2 is: 0.  
```  
  
##  <a name="crbegin"></a>hash_set::crbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca const iteratora adresowania pierwszym elementem w odwróconej hash_set.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [hash_set](../standard-library/hash-set-class.md) lub adresowania co była ostatnim elementem w stałe `hash_set`.  
  
### <a name="remarks"></a>Uwagi  
 `crbegin`jest używany z odwróconej hash_set — podobnie jak [hash_set::begin](#begin) jest używany z hash_set.  
  
 Z wartością zwracaną z `crbegin`, `hash_set` obiektu nie może być modyfikowany.  
  
 `crbegin`może służyć do iterowania po `hash_set` Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_crbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crbegin( );  
   cout << "The first element in the reversed hash_set is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_set is 30.  
```  
  
##  <a name="crend"></a>hash_set::crend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_set —.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [hash_set](../standard-library/hash-set-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `hash_set`).  
  
### <a name="remarks"></a>Uwagi  
 `crend`jest używany z odwróconej `hash_set` podobnie jak [hash_set::end](#end) jest używany z `hash_set`.  
  
 Z wartością zwracaną z `crend`, `hash_set` obiektu nie może być modyfikowany.  
  
 `crend`można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego `hash_set`.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_crend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crend( );  
   hs1_crIter--;  
   cout << "The last element in the reversed hash_set is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_set is 10.  
```  
  
##  <a name="difference_type"></a>hash_set::difference_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów hash_set w zakresie między elementami wskazywana przez Iteratory.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie [ `first`, `last`) między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakres elementów do , ale bez tego elementu wskazywanego przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez kontenery odwracalny, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez podany przez kontener dostępie swobodnym, takich jak wektorowa lub deque — Iteratory dostęp losowy.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;  
  
   hs1.insert( 20 );  
   hs1.insert( 10 );  
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique  
  
   hs1_bIter = hs1.begin( );  
   hs1_eIter = hs1.end( );  
  
   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );  
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );  
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );  
  
   // The keys, and hence the elements, of a hash_set are unique,  
   // so there is at most one of a given value  
   cout << "The number '5' occurs " << df_typ5  
        << " times in hash_set hs1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in hash_set hs1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in hash_set hs1.\n";  
  
   // Count the number of elements in a hash_set  
   hash_set <int>::difference_type  df_count = 0;  
   hs1_Iter = hs1.begin( );  
   while ( hs1_Iter != hs1_eIter)  
   {  
      df_count++;  
      hs1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_set hs1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in hash_set hs1.  
The number '10' occurs 1 times in hash_set hs1.  
The number '20' occurs 1 times in hash_set hs1.  
The number of elements in the hash_set hs1 is: 2.  
```  
  
##  <a name="emplace"></a>hash_set::emplace  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Wstawia element zbudowane w miejscu do hash_set.  
  
```  
template <class ValTy>  
pair <iterator, bool>  
emplace(
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Wartość elementu ma zostać wstawiony do [hash_set](../standard-library/hash-set-class.md) chyba że `hash_set` zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `emplace` Funkcji członkowskiej zwraca parę których `bool` składnik zwraca `true` Jeśli wstawiania była marka i `false` Jeśli `hash_set` już zawiera element, którego klucz ma wartość równoważną w kolejności i których składnik iteratora zwraca adres, gdzie dodano nowego elementu lub którym element został już znajduje się.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_emplace.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<string> hs3;  
   string str1("a");  
  
   hs3.emplace(move(str1));  
   cout << "After the emplace insertion, hs3 contains "  
      << *hs3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hs3 contains a.  
```  
  
##  <a name="emplace_hint"></a>hash_set::emplace_hint  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Wstawia element zbudowane w miejscu do hash_set.  
  
```  
template <class ValTy>  
iterator emplace(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Wartość elementu ma zostać wstawiony do [hash_set](../standard-library/hash-set-class.md) chyba że `hash_set` zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
|`_Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.)|  
  
### <a name="return-value"></a>Wartość zwracana  
 [Hash_set::emplace](#emplace) funkcją członkowską zwracającą iterator wskazującą położenie, w którym wstawiono nowy element do `hash_set`, gdzie znajduje się istniejącego elementu z równoważne porządkowanie lub.  
  
### <a name="remarks"></a>Uwagi  
 Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_emplace_hint.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<string> hs3;  
   string str1("a");  
  
   hs3.insert(hs3.begin(), move(str1));  
   cout << "After the emplace insertion, hs3 contains "  
      << *hs3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hs3 contains a.  
```  
  
##  <a name="empty"></a>hash_set::Empty  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Testy, jeśli hash_set jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli hash_set jest pusta. **false** Jeśli hash_set nie jest pusty.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_empty.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2;  
   hs1.insert ( 1 );  
  
   if ( hs1.empty( ) )  
      cout << "The hash_set hs1 is empty." << endl;  
   else  
      cout << "The hash_set hs1 is not empty." << endl;  
  
   if ( hs2.empty( ) )  
      cout << "The hash_set hs2 is empty." << endl;  
   else  
      cout << "The hash_set hs2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_set hs1 is not empty.  
The hash_set hs2 is empty.  
```  
  
##  <a name="end"></a>hash_set::end  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_set iteratora.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_set. Jeśli hash_set jest pusty, a następnie hash_set::end == hash_set::begin.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnął koniec jego hash_set. Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_end.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: iterator hs1_Iter;  
   hash_set <int> :: const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_Iter = hs1.end( );  
   hs1_Iter--;  
   cout << "The last element of hs1 is " << *hs1_Iter << endl;  
  
   hs1.erase( hs1_Iter );  
  
   // The following 3 lines would err because the iterator is const:  
   // hs1_cIter = hs1.end( );  
   // hs1_cIter--;  
   // hs1.erase( hs1_cIter );  
  
   hs1_cIter = hs1.end( );  
   hs1_cIter--;  
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The last element of hs1 is 3  
The last element of hs1 is now 2  
```  
  
##  <a name="equal_range"></a>hash_set::equal_range  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca parę Iteratory odpowiednio do pierwszego elementu w skrót ustawić za pomocą klucza jest taka sama określonego klucza i pierwszy element mieszania ustawić za pomocą klucza, która jest większa niż klucz.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_set przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para Iteratory, w których pierwsza to [lower_bound](../standard-library/set-class.md#lower_bound) klucz, a drugi jest [upper_bound](../standard-library/set-class.md#upper_bound) klucza.  
  
 Aby uzyskać dostęp do pierwszego iterator ściągnięcia pary zwracane przez funkcję elementu członkowskiego, należy użyć `pr`. **pierwszy**i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi**i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_equal_range.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
   using namespace stdext;  
   typedef hash_set<int> IntHSet;  
   IntHSet hs1;  
   hash_set <int> :: const_iterator hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;  
   p1 = hs1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the hash_set hs1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the hash_set hs1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   hs1_RcIter = hs1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *hs1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = hs1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key greater than or equal to 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.  
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.  
```  
  
##  <a name="erase"></a>hash_set::ERASE  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Usuwa element lub zakres elementów w hash_set z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Położenie elementu do usunięcia z hash_set.  
  
 `first`  
 Pozycja pierwszego elementu usunięte z hash_set.  
  
 `last`  
 Pozycja poza ostatni element usunięty z hash_set.  
  
 `key`  
 Klucz elementów do usunięcia z hash_set.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostała poza wszelkie elementy usunięte lub wskaźnika do końca hash_set nie zawiera żadnego takiego elementu. Trzeci funkcji elementu członkowskiego, liczba elementów, które zostały usunięte z hash_set.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie nigdy nie zgłaszają wyjątków.  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_set::erase.  
  
```  
// hash_set_erase.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_set<int> hs1, hs2, hs3;  
    hash_set<int>::iterator pIter, Iter1, Iter2;  
    int i;  
    hash_set<int>::size_type n;  
  
    for (i = 1; i < 5; i++)  
    {  
        hs1.insert (i);  
        hs2.insert (i * i);  
        hs3.insert (i - 1);  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hs1.begin();  
    hs1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, the hash_set hs1 is:";  
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hs2.begin();  
    Iter2 = --hs2.end();  
    hs2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_set hs2 is:";  
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hs3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted, "  
         << "the hash_set hs3 is:";  
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hs3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hs3.begin();  
    hs3.erase(Iter1);  
  
    cout << "After another element (unique for hash_set) with a key "  
         << endl;  
    cout  << "equal to that of the 2nd element is deleted, "  
          << "the hash_set hs3 is:";  
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.  
After the middle two elements are deleted, the hash_set hs2 is: 16 4.  
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.  
The number of elements removed from hs3 is: 1.  
After another element (unique for hash_set) with a key   
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.  
```  
  
##  <a name="find"></a>hash_set::Find  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora adresowania położenie elementu w hash_set, który ma klucz równoważne z określonym kluczem.  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu wartością klucza sortowania z elementem z hash_set przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` który adresy lokalizacji elementu równoważne z określonym kluczem lub który adresów lokalizacji pomyślne ostatnim elementem w hash_set, jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcją członkowską zwracającą iterator, którego dotyczy element hash_set, którego klucz sortowania jest **równoważne** do argumentu klucz w obszarze binarny predykatu wywołujące kolejność oparty na mniej-niż porównywalności relacji.  
  
 Jeśli wartość zwracana **znaleźć** jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, można zmodyfikować obiektu hash_set.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_find.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.find( 20 );  
   cout << "The element of hash_set hs1 with a key of 20 is: "  
        << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.find( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key of 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // The element at a specific location in the hash_set can be found   
   // by using a dereferenced iterator addressing the location  
   hs1_AcIter = hs1.end( );  
   hs1_AcIter--;  
   hs1_RcIter = hs1.find( *hs1_AcIter );  
   cout << "The element of hs1 with a key matching "  
        << "that of the last element is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_set hs1 with a key of 20 is: 20.  
The hash_set hs1 doesn't have an element with a key of 40.  
The element of hs1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>hash_set::get_allocator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca kopię obiektu alokatora użyta do skonstruowania hash_set.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Program przydzielania służy do zarządzania pamięci, która jest parametr szablonu hash_set `Allocator`.  
  
 Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy hash_set — Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_set <int, hash_compare <int, less<int> > > hs1;  
   hash_set <int,  hash_compare <int, greater<int> > > hs2;  
   hash_set <double, hash_compare <double,  
      less<double> >, allocator<double> > hs3;  
  
   hash_set <int, hash_compare <int,  
      greater<int> > >::allocator_type hs2_Alloc;  
   hash_set <double>::allocator_type hs3_Alloc;  
   hs2_Alloc = hs2.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hs1.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hs3.max_size( ) <<  "." << endl;  
  
   // The following lines create a hash_set hs4  
   // with the allocator of hash_set hs1.  
   hash_set <int>::allocator_type hs4_Alloc;  
   hash_set <int> hs4;  
   hs4_Alloc = hs2.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hs2_Alloc == hs4_Alloc )  
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
  
##  <a name="hash_set"></a>hash_set::hash_set  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Konstruuje `hash_set` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `hash_set`.  
  
```  
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,  
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,   
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,   
    const Compare& Comp,   
    const Allocator& Al);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa przydzielania magazynu do użycia dla tego `hash_set` obiektu, który domyślnie `Allocator`.|  
|`Comp`|Funkcja porównywania typu `const Traits` porządkowania elementów w `hash_set`, jakie nie `hash_compare`.|  
|`Right`|`hash_set` Którego zbudowany `hash_set` ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory przechowywania typu obiektu przydzielania, który zarządza przechowywania w pamięci dla `hash_set` i który później może być zwracany przez wywołanie metody [hash_set::get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.  
  
 Wszystkie konstruktory zainicjować ich hash_sets.  
  
 Wszystkie konstruktory przechowywania obiektem funkcji typu `Traits` używany do ustanawiania kolejność kluczy `hash_set` i który później może być zwracany przez wywołanie metody [hash_set::key_comp](#key_comp). Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
 Pierwszy Konstruktor tworzy puste początkowego `hash_set` drugi określa typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów, a trzeci jawnie określa typ alokatora ( `Al`) jako używane. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.  
  
 Konstruktory czwartym i piątym Określ kopię `hash_set` `Right`.  
  
 Ostatni szóstego, siódmego i ósmego konstruktorów Użyj initializer_list dla elementów.  
  
 Skopiuj konstruktorów ostatni zakres [ `First`, `Last`) z `hash_set` rosnącymi explicitness określania typu porównanie funkcji klasa cech i przydzielania.  
  
 Przenosi ósmego konstruktora `hash_set` `Right`.  
  
 Rzeczywiste kolejność elementów `hash_set` kontenera jest zależny od funkcji skrótu, funkcja porządkowania skrót bieżący rozmiar tabeli i ogólnie rzecz biorąc, nie można przewidzieć, ponieważ może to z kontenerem zestawu, w której była określana przez kolejność Funkcja samodzielnie.  
  
##  <a name="insert"></a>hash_set::INSERT  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Wstawia element lub zakres elementów do `hash_set`.  
  
```  
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,  
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)  
template <class InputIterator>  
void insert(
    InputIterator First,  
    InputIterator Last);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Val`|Wartość elementu ma zostać wstawiony do `hash_set` chyba że `hash_set` zawiera już ten element lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania.|  
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.)|  
|`First`|Pozycja pierwszego elementu skopiowane z `hash_set`.|  
|`Last`|Pozycja poza ostatni element do skopiowania z `hash_set`.|  
|`IList`|Lista initializer_list, z której mają być skopiowane elementy.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy `insert` funkcji członkowskiej zwraca parę których `bool` składnik zwraca `true` Jeśli wstawiania była marka i `false` Jeśli `hash_set` już zawiera element, którego klucz ma wartość równoważną w kolejności, i którego składnik iteratora zwraca adres, gdzie dodano nowego elementu lub którym element został już znajduje się.  
  
 Aby dostęp do składnika iterator pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr.first` i aby odwołania do niego, należy użyć `*(pr.first)`. Aby uzyskać dostęp do `bool` składnika pary `pr` zwracane przez tę funkcję elementu członkowskiego, użyj `pr.second`i aby odwołania do niego, należy użyć `*(pr.second)`.  
  
 Drugi `insert` funkcją członkowską zwracającą iterator wskazującą położenie, w którym wstawiono nowy element do `hash_set`.  
  
### <a name="remarks"></a>Uwagi  
 Trzeci funkcji członkowskiej Wstawia elementy initializer_list.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji wartości elementów w `hash_set` odpowiadający każdemu elementowi adresowane przez iterator w zakresie [ `First`, `Last`) z określonej `hash_set`.  
  
##  <a name="iterator"></a>hash_set::iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **iterator** może służyć do modyfikowania wartości elementu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_comp"></a>hash_set::key_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Pobiera kopię obiektu cech mieszania używany do wyznaczania wartości skrótu i kolejność elementu wartości klucza w hash_set.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcji, który hash_set używa do porządkowania swoich elementów, czyli parametru szablonu `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **const klucza &** _ *xVal*, **const klucza &** \_ `yVal`);  
  
 która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla klasy hash_set i hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_key_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int, hash_compare < int, less<int> > >hs1;  
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1  
          = hs1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of hs1."  
           << endl;  
   }  
   else  
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of hs1."  
        << endl;  
   }  
  
   hash_set <int, hash_compare < int, greater<int> > > hs2;  
   hash_set<int, hash_compare < int, greater<int> > >::key_compare  
         kc2 = hs2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if(result2 == true)  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of hs2."  
           << endl;  
   }  
   else  
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of hs2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>hash_set::key_compare  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_set.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 `key_compare`synonim parametru szablonu jest `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
 Należy pamiętać, że oba `key_compare` i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="key_type"></a>hash_set::key_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który opisuje obiekt zapisany jako elementu hash_set jako klucza sortowania.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 **key_type** jest synonimem parametru szablonu `Key`.  
  
 Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
 Należy pamiętać, że oba `key_type` i [value_type](#value_type) są synonimy dla parametru szablonu **klucza**. Oba typy są dostępne dla klasy hash_set i hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.  
  
##  <a name="lower_bound"></a>hash_set::lower_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca pierwszy element w hash_set — iteratora klucz, który jest równy lub większy niż określony klucz.  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_set przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` który adresy lokalizacji elementu w hash_set, że za pomocą klucza, która jest równa lub większa niż klucz argumentu lub który adresów lokalizacji pomyślne ostatnim elementem w hash_set, jeśli nie są zgodne Znaleziono dla klucza.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.lower_bound( 20 );  
   cout << "The element of hash_set hs1 with a key of 20 is: "  
        << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key of 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_set can be found   
   // by using a dereferenced iterator that addresses the location  
   hs1_AcIter = hs1.end( );  
   hs1_AcIter--;  
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );  
   cout << "The element of hs1 with a key matching "  
        << "that of the last element is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_set hs1 with a key of 20 is: 20.  
The hash_set hs1 doesn't have an element with a key of 40.  
The element of hs1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a>hash_set::max_size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca maksymalną długość hash_set.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe hash_set.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_max_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::size_type i;  
  
   i = hs1.max_size( );  
   cout << "The maximum possible length "  
        << "of the hash_set is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>hash_set::operator =  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zamienia elementy hash_set kopię hash_set innego.  
  
```  
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Hash_set](../standard-library/hash-set-class.md) kopiowane do `hash_set`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `hash_set`, `operator=` albo kopiuje lub przenosi zawartość `right` do `hash_set`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_operator_as.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<int> v1, v2, v3;  
   hash_set<int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>hash_set::Pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który dostarcza wskaźnik do elementu hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie hash_set.  
  
   
  
##  <a name="rbegin"></a>hash_set::rbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora adresowania pierwszym elementem w hash_set odwróconej.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego adresowania pierwszym elementem w odwróconej hash_set lub adresowania co była ostatnim elementem w hash_set stałe.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin`jest używany z odwróconej hash_set — podobnie jak [rozpocząć](#begin) jest używany z hash_set.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu hash_set.  
  
 `rbegin`może służyć do iterowania po hash_set Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_rbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::reverse_iterator hs1_rIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_rIter = hs1.rbegin( );  
   cout << "The first element in the reversed hash_set is "  
        << *hs1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a hash_set in a forward order  
   cout << "The hash_set is: ";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
      cout << *hs1_Iter << " ";  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a hash_set in a reverse order  
   cout << "The reversed hash_set is: ";  
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );  
         hs1_rIter++ )  
      cout << *hs1_rIter << " ";  
   cout << endl;  
  
   // A hash_set element can be erased by dereferencing to its key   
   hs1_rIter = hs1.rbegin( );  
   hs1.erase ( *hs1_rIter );  
  
   hs1_rIter = hs1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_set is "<< *hs1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_set is 30.  
The hash_set is: 10 20 30   
The reversed hash_set is: 30 20 10   
After the erasure, the first element in the reversed hash_set is 20.  
```  
  
##  <a name="reference"></a>hash_set::Reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który zawiera odwołanie do elementu przechowywane w hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   int &Ref1 = *hs1.begin( );  
  
   cout << "The first element in the hash_set is "  
        << Ref1 << "." << endl;  
  
   // The value of the 1st element of the hash_set can be changed  
   // by operating on its (non-const) reference  
   Ref1 = Ref1 + 5;  
  
   cout << "The first element in the hash_set is now "  
        << *hs1.begin() << "." << endl;  
}  
```  
  
```Output  
The first element in the hash_set is 10.  
The first element in the hash_set is now 15.  
```  
  
##  <a name="rend"></a>hash_set::rend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_set iteratora.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_set (lokalizacja miał przed pierwszym elementem w stałe hash_set).  
  
### <a name="remarks"></a>Uwagi  
 `rend`jest używany z odwróconej hash_set — podobnie jak [zakończenia](#end) jest używany z hash_set.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu hash_set. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu hash_set. Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
 `rend`można sprawdzać, czy osiągnął koniec jego hash_set odwrotnej iteratora.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_rend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::reverse_iterator hs1_rIter;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   cout << "The last element in the reversed hash_set is "  
        << *hs1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // throught a hash_set in a forward order  
   cout << "The hash_set is: ";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
      cout << *hs1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // through a hash_set in a reverse order  
   cout << "The reversed hash_set is: ";  
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );  
         hs1_rIter++ )  
      cout << *hs1_rIter << " ";  
   cout << "." << endl;  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   hs1.erase ( *hs1_rIter );  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   cout << "After the erasure, the last element in the "  
        << "reversed hash_set is " << *hs1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_set is 10.  
The hash_set is: 10 20 30 .  
The reversed hash_set is: 30 20 10 .  
After the erasure, the last element in the reversed hash_set is 20.  
```  
  
##  <a name="reverse_iterator"></a>hash_set::reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` umożliwia iterację hash_set — odwrotnie.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="size"></a>hash_set::size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca liczbę elementów w hash_set.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość hash_set.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: size_type i;  
  
   hs1.insert( 1 );  
   i = hs1.size( );  
   cout << "The hash_set length is " << i << "." << endl;  
  
   hs1.insert( 2 );  
   i = hs1.size( );  
   cout << "The hash_set length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_set length is 1.  
The hash_set length is now 2.  
```  
  
##  <a name="size_type"></a>hash_set::size_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w hash_set.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie`size_type`  
  
##  <a name="swap"></a>hash_set::swap  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zamienia hash_sets dwa elementy.  
  
```  
void swap(hash_set& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_set — argument, zapewniając elementy, aby być zamieniona na hash_set docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch hash_sets, której elementy są wymieniane.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_swap.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2, hs3;  
   hash_set <int>::iterator hs1_Iter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
   hs2.insert( 100 );  
   hs2.insert( 200 );  
   hs3.insert( 300 );  
  
   cout << "The original hash_set hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hs1.swap( hs2 );  
  
   cout << "After swapping with hs2, list hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hs1, hs3 );  
  
   cout << "After swapping with hs3, list hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_set hs1 is: 10 20 30.  
After swapping with hs2, list hs1 is: 200 100.  
After swapping with hs3, list hs1 is: 300.  
```  
  
##  <a name="upper_bound"></a>hash_set::upper_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Zwraca iteratora do pierwszego elementu w hash_set który za pomocą klucza, który jest większy niż określony klucz.  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_set przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Iterator** lub `const_iterator` który adresy lokalizacji elementu w hash_set, że za pomocą klucza, która jest równa lub większa niż klucz argumentu, lub który adresów lokalizacji pomyślne ostatnim elementem w hash_set, jeśli nie są zgodne Znaleziono dla klucza.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.upper_bound( 20 );  
   cout << "The first element of hash_set hs1 with a key greater "  
        << "than 20 is: " << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key greater than 30." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key > 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_set can be found  
   // by using a dereferenced iterator addressing the location  
   hs1_AcIter = hs1.begin( );  
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );  
   cout << "The first element of hs1 with a key greater than "  
        << endl << "that of the initial element of hs1 is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of hash_set hs1 with a key greater than 20 is: 30.  
The hash_set hs1 doesn't have an element with a key greater than 30.  
The first element of hs1 with a key greater than   
that of the initial element of hs1 is: 20.  
```  
  
##  <a name="value_comp"></a>hash_set::value_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Pobiera kopię porównania obiekt używany do wartości elementu kolejności w hash_set.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcji, który hash_set używa do porządkowania swoich elementów, czyli parametru szablonu `Compare`.  
  
 Aby uzyskać więcej informacji na temat `Compare`, zobacz sekcję uwag [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego:  
  
 **bool operator**( **const klucza &** _ *xVal*, **const klucza &** \_ `yVal`);  
  
 która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.  
  
 Należy pamiętać, że oba [value_compare](../standard-library/set-class.md#value_compare) i [key_compare](../standard-library/set-class.md#key_compare) są synonimy dla parametru szablonu `Compare`. Oba typy są dostępne dla klasy hash_set i hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_value_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int, hash_compare < int, less<int> > > hs1;  
   hash_set <int, hash_compare < int, less<int> >  >::value_compare  
      vc1 = hs1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )  
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of hs1."  
           << endl;  
   }  
   else  
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of hs1."  
           << endl;  
   }  
  
   hash_set <int, hash_compare < int, greater<int> > > hs2;  
   hash_set<int, hash_compare < int, greater<int> > >::value_compare  
      vc2 = hs2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )  
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of hs2."  
           << endl;  
   }  
   else  
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of hs2."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_compare"></a>hash_set::value_compare  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ zawiera dwa obiekty funkcji, binary predykatu porównania klasy, które można porównać dwóch wartości elementu hash_set, aby określić ich kolejność względną i predykat jednoargumentowe, który tworzy skrót elementy.  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 **value_compare** jest synonimem parametru szablonu `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_set — klasa](../standard-library/hash-set-class.md) tematu.  
  
 Należy pamiętać, że oba [key_compare](#key_compare) i **value_compare** są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla klasy hash_set i hash_multiset, gdy są identyczne dla zgodności z klasy hash_map i hash_multimap, gdy są one różne.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_comp](#value_comp) przykład sposobu deklarowanie i użycie `value_compare`.  
  
##  <a name="value_type"></a>hash_set::value_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).  
  
 Typ, który opisuje obiekt zapisany jako elementu hash_set jako wartość.  
  
```  
typedef Key value_type;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_set_value_type.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
  
   hash_set <int> :: value_type hsvt_Int;   // Declare value_type  
   hsvt_Int = 10;             // Initialize value_type  
  
   hash_set <int> :: key_type hskt_Int;   // Declare key_type  
   hskt_Int = 20;             // Initialize key_type  
  
   hs1.insert( hsvt_Int );         // Insert value into hs1  
   hs1.insert( hskt_Int );         // Insert key into hs1  
  
   // A hash_set accepts key_types or value_types as elements  
   cout << "The hash_set has elements:";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)  
      cout << " " << *hs1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The hash_set has elements: 10 20.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

