---
title: "hash_multimap — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6474bd6cdbb8baa2819d80f122b5a17792251bc
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="hashmultimap-class"></a>hash_multimap — Klasa
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Hash_multimap — klasa kontenera jest rozszerzeniem standardowa biblioteka C++ i jest używany do przechowywania i szybkie pobieranie danych z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość nie musi być unikatowa i wartość skojarzonych danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Key,   
    class Type,   
    class Traits=hash_compare <Key, less <Key>>,   
    class Allocator=allocator <pair  <const Key, Type>>>  
class hash_multimap  
```  
  
#### <a name="parameters"></a>Parametry  
 `Key`  
 Typ danych klucza mają być przechowywane w hash_multimap.  
  
 `Type`  
 Typ danych elementu mają być przechowywane w hash_multimap.  
  
 `Traits`  
 Typ, który obejmuje dwa obiekty funkcji, co klasa `Traits` jest możliwe do porównania dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względną i funkcji skrótu, która jest jednoargumentowy predykatu mapowania wartości klucza elementy do liczb całkowitych bez znaku z Typ **size_t**. Ten argument jest opcjonalny i `hash_compare<Key, less<Key>>` jest wartością domyślną.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji hash_multimap i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type>>`.  
  
## <a name="remarks"></a>Uwagi  
 Hash_multimap — jest:  
  
-   Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.  
  
-   Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.  
  
-   Wartość skrótu, ponieważ jej elementy są pogrupowane w pakiety na podstawie wartości funkcji skrótu zastosowane do wartości kluczy elementów.  
  
-   Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.  
  
-   Kontener asocjacyjnej pary, ponieważ jego wartości elementu różnią się od jego wartości klucza.  
  
-   Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.  
  
 Główną zaletą tworzenia skrótów za pośrednictwem sortowanie jest większą wydajność; wykonuje wstawienia, usuwanie i wyszukuje w stałej Średni czas w porównaniu z danej chwili proporcjonalna do logarytmu liczba elementów w kontenerze sortowania techniki pomyślnego tworzenia skrótów. Wartość elementu w hash_multimap, ale nie skojarzone wartości klucza, można zmienić bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.  
  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjna skrótu są zoptymalizowane pod kątem operacji wyszukiwania, wstawiania i usuwania. Funkcje Członkowskie, które jawnie obsługują te operacje są wydajne, gdy jest używany z funkcji skrótu dobrze zaprojektowanego, wykonywanie ich w czasie, który jest średnio stała i nie jest zależna od liczby elementów w kontenerze. Funkcja skrótu dobrze zaprojektowanego tworzy uniform rozkład wartości skrótu i minimalizuje liczbę konfliktów, gdzie jest określany kolizji występuje, gdy różne wartości klucza są zamapowane na tę samą wartość skrótu. W najgorszym przypadku przy użyciu najgorszy funkcji skrótu to możliwe liczba operacji jest proporcjonalna do liczby elementów w sekwencji (czas liniowej).  
  
 Hash_multimap — powinien być asocjacyjnej kontener wyboru po spełnieniu warunków kojarzenie wartości z ich kluczy przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego należy tak, aby klucze były unikatowe słowa kluczowe zostały zdefiniowane unikatowo, hash_map byłoby kontener wyboru. Jeśli z drugiej strony, są przechowywane tylko listę słów, hash_set będzie poprawny kontenera. W przypadku wielu wystąpień słowa były dozwolone, hash_multiset byłoby struktury odpowiedniego kontenera.  
  
 Hash_multimap porządkuje sekwencji kontroluje wywołując skrótu przechowywaną `Traits` typu obiektu [value_compare](../standard-library/value-compare-class.md). Ten obiekt przechowywane, mogą być używane przez wywołanie funkcji Członkowskich [key_comp](../standard-library/hash-map-class.md#key_comp). Obiekt funkcji musi działają tak samo, jak obiekt klasy [hash_compare —](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. W szczególności dla wszystkich wartości `Key` typu `Key`, wywołanie `Traits (Key)` daje rozkład wartości typu `size_t`.  
  
 Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Powoduje to kolejność między elementami odpowiednika. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne f (x, y) jest obiektem funkcji, która ma dwa obiekty argument `x` i `y` i wartością zwracaną `true` lub `false`. Kolejność na hash_multimap jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy oba f (x y) i f (y, x) są `false`. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.  
  
 Rzeczywiste kolejność elementów w kontrolowanej sekwencji zależy od funkcji skrótu, funkcja porządkowania i bieżący rozmiar tablicy skrótów przechowywane w obiekcie kontenera. Nie można ustalić bieżący rozmiar tablicy skrótów, więc nie można przewidzieć ogólnie kolejność elementów w kontrolowanej sekwencji. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.  
  
 Iterator dostarczonych przez hash_multimap — klasa jest iteratora dwukierunkowego, ale funkcji elementów członkowskich klasy [Wstaw](#insert) i [hash_multimap](#hash_multimap) wersje przyjmować jako parametry szablonu słabszych danych wejściowych Iterator, którego wymagania funkcji są bardziej minimalne niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma własną hash_multimap wymagania i algorytmy, które współpracują z nich należy ograniczyć ich założenia wymagania udostępniane przez ten typ iteratora. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny hash_multimap funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory `[First, Last)` w kontekście funkcji elementów członkowskich.  
  
   
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[hash_multimap](#hash_multimap)|Tworzy listę o określonym rozmiarze lub elementów określonej wartości na lub z określonym `allocator` lub jako kopię innymi `hash_multimap`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `hash_multimap` obiektu.|  
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_multimap`.|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element `hash_multimap`.|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w `hash_multimap` do odczytu i wykonywania `const` operacji.|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `hash_multimap`.|  
|[difference_type](#difference_type)|Wpisz liczbę całkowitą ze znakiem, służący do reprezentowania liczbę elementów `hash_multimap` w zakresie między elementami wskazywana przez Iteratory.|  
|[iterator](#iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w `hash_multimap`.|  
|[key_compare](#key_compare)|Typ, który zawiera obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `hash_multimap`.|  
|[key_type](#key_type)|Typ, który opisuje obiektu klucza sortowania, który stanowi każdy element `hash_multimap`.|  
|[mapped_type](#mapped_type)|Typ reprezentujący typ danych przechowywanych w `hash_multimap`.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu `hash_multimap`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `hash_multimap`.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `hash_multimap`.|  
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `hash_multimap`.|  
|[value_type](#value_type)|Typ, który zawiera obiekt funkcji, który można porównać dwóch elementów jako klucze sortowania, aby określić ich kolejność względne w `hash_multimap`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[begin](#begin)|Zwraca iteratora adresowania pierwszym elementem w `hash_multimap`.|  
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w `hash_multimap`.|  
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `hash_multimap`.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy `hash_multimap`.|  
|[Liczba](#count)|Zwraca liczbę elementów w `hash_multimap` którego klucz odpowiada parametr określony klucz.|  
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszym elementem w odwróconej `hash_multimap`.|  
|[crend](#crend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej `hash_multimap`.|  
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `hash_multimap`.|  
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `hash_multimap`, ze wskazówką umieszczania.|  
|[empty](#empty)|Sprawdza, czy `hash_multimap` jest pusta.|  
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `hash_multimap`.|  
|[equal_range](#equal_range)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `hash_multimap`.|  
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `hash_multimap` od określonej pozycji|  
|[Znajdź](#find)|Zwraca iteratora adresowania położenie elementu w `hash_multimap` mający klucz równoważne z określonym kluczem.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` użyty do utworzenia obiektu `hash_multimap`.|  
|[insert](#insert)|Wstawia element lub zakres elementów do `hash_multimap` na określonej pozycji.|  
|[key_comp](#key_comp)|Pobiera kopię porównania obiekt używany do kolejność kluczy w `hash_multimap`.|  
|[lower_bound](#lower_bound)|Zwraca pierwszy element w iteratora `hash_multimap` czy za pomocą klucza wartość jest równa lub większa niż określony klucz.|  
|[max_size](#max_size)|Zwraca maksymalną długość `hash_multimap`.|  
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszym elementem w odwróconej `hash_multimap`.|  
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej `hash_multimap`.|  
|[Rozmiar](#size)|Określa nowy rozmiar `hash_multimap`.|  
|[swap](#swap)|Zamienia elementy dwóch `hash_multimap`s.|  
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `hash_multimap` czy za pomocą klucza wartość jest większa niż określony klucz.|  
|[value_comp](#value_comp)|Pobiera kopię porównania obiekt używany do wartości elementu kolejności w `hash_multimap`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[hash_multimap::operator=](#op_eq)|Zastępuje elementy `hash_multimap` z kopią innego `hash_multimap`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<hash_map >  
  
 **Namespace:** stdext —  
  
##  <a name="allocator_type"></a>  hash_multimap::allocator_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który reprezentuje klasę alokatora dla obiekt hash_multimap.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `allocator_type` synonim parametru szablonu jest `Allocator`.  
  
 Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą `allocator_type`.  
  
##  <a name="begin"></a>  hash_multimap::BEGIN  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca adresowania pierwszym elementem w hash_multimap iteratora.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adresowanie pierwszym elementem w hash_multimap lub lokalizacji pomyślne pusty hash_multimap iteratora dwukierunkowego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować elementów w obiekcie hash_multimap. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iterator**, elementów w obiekcie hash_multimap może być modyfikowany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_begin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 0, 0 ) );  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.begin ( );  
   cout << "The first element of hm1 is " << hm1_cIter -> first   
        << "." << endl;  
  
   hm1_Iter = hm1.begin ( );  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.begin ( );  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.begin( );  
   cout << "The first element of hm1 is now " << hm1_cIter -> first   
        << "." << endl;  
}  
```  
  
```Output  
The first element of hm1 is 0.  
The first element of hm1 is now 1.  
```  
  
##  <a name="cbegin"></a>  hash_multimap::cbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca const iteratora adresowania pierwszym elementem w hash_multimap.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego adresowania pierwszym elementem w [hash_multimap](../standard-library/hash-multimap-class.md) lub lokalizacji pomyślne pustą `hash_multimap`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_cbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.cbegin ( );  
   cout << "The first element of hm1 is "   
        << hm1_cIter -> first << "." << endl;  
   }  
```  
  
```Output  
The first element of hm1 is 2.  
```  
  
##  <a name="cend"></a>  hash_multimap::cend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w hash_multimap —.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Const iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w [hash_multimap](../standard-library/hash-multimap-class.md). Jeśli `hash_multimap` jest pusta, następnie `hash_multimap::cend == hash_multimap::begin`.  
  
### <a name="remarks"></a>Uwagi  
 `cend` Służy do sprawdzenia, czy iteratora osiągnął koniec jego hash_multimap.  
  
 Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_cend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.cend( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
   }  
```  
  
```Output  
The value of last element of hm1 is 30.  
```  
  
##  <a name="clear"></a>  hash_multimap::Clear  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Usuwa wszystkie elementy hash_multimap.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multimap::clear.  
  
```  
// hash_multimap_clear.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 4));  
  
    i = hm1.size();  
    cout << "The size of the hash_multimap is initially "  
         << i  << "." << endl;  
  
    hm1.clear();  
    i = hm1.size();  
    cout << "The size of the hash_multimap after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the hash_multimap is initially 2.  
The size of the hash_multimap after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  hash_multimap::const_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_multimap.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
 `const_iterator` Zdefiniowany przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair`  *\< ***constKey, typ*** >* . Wartość klucza jest dostępna za pośrednictwem pierwszego pary — członek, a wartość elementu zamapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.  
  
 Aby usunąć odwołania do `const_iterator` `cIter` wskazuje element hash_multimap, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `cIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `cIter`  ->  **drugi**, który jest odpowiednikiem (\* `cIter`). **pierwszy**.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) na przykład za pomocą `const_iterator`.  
  
##  <a name="const_pointer"></a>  hash_multimap::const_pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który dostarcza wskaźnik do **const** element hash_multimap.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie hash_multimap.  
  
   
  
##  <a name="const_reference"></a>  hash_multimap::const_reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który zawiera odwołanie do **const** element przechowywane w hash_multimap do odczytu i wykonywania **const** operacji.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_const_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin() -> second );  
  
   cout << "The data value of 1st element in the hash_multimap is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of 1st element in the hash_multimap is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element hash_multimap.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację hash_multimap — odwrotnie.  
  
 `const_reverse_iterator` Zdefiniowany przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair` * \< * **const klucza, wpisz >**, którego pierwszego elementu członkowskiego ma kluczowe znaczenie dla elementu i którego drugi element członkowski jest mapowanych datum posiadanych przez element.  
  
 Aby usunąć odwołania do `const_reverse_iterator` `crIter` wskazuje element hash_multimap, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `crIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `crIter`  ->  **drugi**, który jest odpowiednikiem (\* `crIter`). **pierwszy**.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.  
  
##  <a name="count"></a>  hash_multimap::Count  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca liczbę elementów w hash_multimap, którego klucz odpowiada parametr określony klucz.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz elementu do dopasowania z hash_multimap.  
  
### <a name="return-value"></a>Wartość zwracana  
 1, jeśli hash_multimap zawiera element, którego klucz sortowania pasuje do klucza parametr; 0, jeśli hash_multimap nie zawiera element z kluczem dopasowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów w zakresie  
  
 **[lower_bound (** `key` **), upper_bound (** `key` **))**  
  
 które mają wartość klucza `key`.  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multimap::count.  
  
```  
// hash_multimap_count.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 1));  
    hm1.insert(Int_Pair(1, 4));  
    hm1.insert(Int_Pair(2, 1));  
  
    // Elements do not need to have unique keys in hash_multimap,  
    // so duplicates are allowed and counted  
    i = hm1.count(1);  
    cout << "The number of elements in hm1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hm1.count(2);  
    cout << "The number of elements in hm1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = hm1.count(3);  
    cout << "The number of elements in hm1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hm1 with a sort key of 1 is: 2.  
The number of elements in hm1 with a sort key of 2 is: 2.  
The number of elements in hm1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>  hash_multimap::crbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca const iteratora adresowania pierwszym elementem w odwróconej hash_multimap.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [hash_multimap](../standard-library/hash-multimap-class.md) lub adresowania co była ostatnim elementem w stałe `hash_multimap`.  
  
### <a name="remarks"></a>Uwagi  
 `crbegin` jest używany z odwróconej hash_multimap — podobnie jak [hash_multimap::begin](#begin) jest używany z `hash_multimap`.  
  
 Z wartością zwracaną z `crbegin`, `hash_multimap` obiektu nie może być modyfikowany.  
  
 `crbegin` może służyć do iterowania po `hash_multimap` Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_crbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="crend"></a>  hash_multimap::crend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multimap —.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [hash_multimap](../standard-library/hash-multimap-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `hash_multimap`).  
  
### <a name="remarks"></a>Uwagi  
 `crend` jest używany z odwróconej hash_multimap — podobnie jak [hash_multimap::end](#end) jest używany z hash_multimap.  
  
 Z wartością zwracaną z `crend`, `hash_multimap` obiektu nie może być modyfikowany.  
  
 `crend` można sprawdzać, czy osiągnął koniec jego hash_multimap odwrotnej iteratora.  
  
 Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_crend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crend( );  
   hm1_crIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="difference_type"></a>  hash_multimap::difference_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów hash_multimap w zakresie między elementami wskazywana przez Iteratory.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie *[Imię, nazwisko)* między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakresu elementy do, z wyjątkiem, element wskazywana przez `last`.  
  
 Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez kontenery odwracalny, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępie swobodnym udostępniane przez kontener dostępie swobodnym, takich jak wektorowa.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_difference_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
#include <algorithm>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(3, 20));  
  
    // The following will insert, because map keys  
    // do not need to be unique  
    hm1.insert(Int_Pair(2, 30));  
  
    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;  
    hm1_bIter = hm1.begin();  
    hm1_eIter = hm1.end();  
  
    // Count the number of elements in a hash_multimap  
    hash_multimap<int, int>::difference_type df_count = 0;  
    hm1_Iter = hm1.begin();  
    while (hm1_Iter != hm1_eIter)  
    {  
        df_count++;  
        hm1_Iter++;  
    }  
  
    cout << "The number of elements in the hash_multimap hm1 is: "  
         << df_count << "." << endl;  
  
    cout << "The keys of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> first;  
    cout << "." << endl;  
  
    cout << "The values of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
The number of elements in the hash_multimap hm1 is: 4.  
The keys of the mapped elements are: 1 2 2 3.  
The values of the mapped elements are: 10 20 30 20.  
```  
  
##  <a name="emplace"></a>  hash_multimap::emplace  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Wstawia element zbudowane w miejscu do hash_multimap.  
  
```  
template <class ValTy>  
iterator emplace(ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element ma zostać wstawiony do skonstruowania wartości używane do przenoszenia [hash_multimap](../standard-library/hash-multimap-class.md).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `emplace` Funkcją członkowską zwracającą iterator wskazujący miejsce, w którym dodano nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 [Hash_multimap::value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_emplace.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(move(is1));  
    cout << "After the emplace, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="emplace_hint"></a>  hash_multimap::emplace_hint  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Wstawia element zbudowane w miejscu do hash_multimap, ze wskazówką umieszczania.  
  
```  
template <class ValTy>  
iterator emplace_hint(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element ma zostać wstawiony do skonstruowania wartości używane do przenoszenia [hash_multimap](../standard-library/hash-multimap-class.md) chyba że `hash_multimap` już zawiera tego elementu (lub, ogólnie rzecz biorąc, element, którego klucz ekwiwalentnie porządkowania).|  
|`_Where`|Wskazówki dotyczące miejsca, aby rozpocząć wyszukiwanie poprawny punkt wstawiania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 [Hash_multimap::emplace](#emplace) funkcją członkowską zwracającą iterator wskazującą położenie, w którym wstawiono nowy element do `hash_multimap`.  
  
### <a name="remarks"></a>Uwagi  
 [Hash_multimap::value_type](#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.  
  
 Wstawiania może wystąpić podczas amortyzowanego stałej, zamiast logarytmicznej czasu, jeśli punkt wstawiania poniższą `_Where`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_emplace_hint.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(hm1.begin(), move(is1));  
    cout << "After the emplace insertion, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="empty"></a>  hash_multimap::Empty  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Testy, jeśli hash_multimap jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli hash_multimap jest pusta. **false** Jeśli hash_multimap nie jest pusty.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_empty.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2;  
  
   typedef pair <int, int> Int_Pair;  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( hm1.empty( ) )  
      cout << "The hash_multimap hm1 is empty." << endl;  
   else  
      cout << "The hash_multimap hm1 is not empty." << endl;  
  
   if ( hm2.empty( ) )  
      cout << "The hash_multimap hm2 is empty." << endl;  
   else  
      cout << "The hash_multimap hm2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_multimap hm1 is not empty.  
The hash_multimap hm2 is empty.  
```  
  
##  <a name="end"></a>  hash_multimap::end  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_multimap iteratora.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w hash_multimap. Jeśli hash_multimap jest pusty, a następnie hash_multimap::end == hash_multimap::begin.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnął koniec jego hash_multimap.  
  
 Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_end.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
  
   hm1_Iter = hm1.end( );  
   hm1_Iter--;  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.end ( );  
   // hm1_cIter--;  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is now "  
        << hm1_cIter -> second << "." << endl;  
}  
```  
  
```Output  
The value of last element of hm1 is 30.  
The value of last element of hm1 is now 20.  
```  
  
##  <a name="equal_range"></a>  hash_multimap::equal_range  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca parę Iteratory odpowiednio do pierwszego elementu w hash_multimap za pomocą klucza, który jest większy niż określony klucz i pierwszy element w hash_multimap za pomocą klucza jest równa lub większa niż klucz.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multimap przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para Iteratory tak, aby był pierwszy [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.  
  
 Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi** i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_equal_range.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_multimap <int, int> IntMMap;  
   IntMMap hm1;  
   hash_multimap <int, int> :: const_iterator hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;  
   p1 = hm1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   hm1_RcIter = hm1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << hm1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = hm1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key less than 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2  
 in the hash_multimap hm1 is: 20.  
The upper bound of the element with a key of 2  
 in the hash_multimap hm1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The hash_multimap hm1 doesn't have an element with a key less than 4.  
```  
  
##  <a name="erase"></a>  hash_multimap::ERASE  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Usuwa element lub zakres elementów w hash_multimap z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Położenie elementu do usunięcia z hash_multimap.  
  
 `first`  
 Pozycja pierwszego elementu usunięte z hash_multimap.  
  
 `last`  
 Pozycja poza ostatni element usunięty z hash_multimap.  
  
 `key`  
 Klucz elementów do usunięcia z hash_multimap.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostała poza wszelkie elementy usunięte lub wskaźnika do końca hash_multimap nie zawiera żadnego takiego elementu.  
  
 Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie nigdy nie zgłaszają wyjątków.  
  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multimap::erase.  
  
```  
// hash_multimap_erase.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2, hm3;  
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_multimap<int, int>::size_type n;  
    typedef pair<int, int> Int_Pair;  
  
    for (i = 1; i < 5; i++)  
    {  
        hm1.insert(Int_Pair (i, i) );  
        hm2.insert(Int_Pair (i, i*i) );  
        hm3.insert(Int_Pair (i, i-1) );  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hm1.begin();  
    hm1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, "  
         << "the hash_multimap hm1 is:";  
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hm2.begin();  
    Iter2 = --hm2.end();  
    hm2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_multimap hm2 is:";  
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    hm3.insert(Int_Pair (2, 5));  
    n = hm3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n"  
         << " the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hm3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hm3.begin();  
    hm3.erase(Iter1);  
  
    cout << "After another element with a key equal to that of the"  
         << endl;  
    cout  << " 2nd element is deleted, "  
          << "the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.  
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.  
After the element with a key of 2 is deleted,  
 the hash_multimap hm3 is: 0 2 3.  
The number of elements removed from hm3 is: 2.  
After another element with a key equal to that of the  
 2nd element is deleted, the hash_multimap hm3 is: 0 3.  
```  
  
##  <a name="find"></a>  hash_multimap::Find  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca iteratora adresowania lokalizację pierwszy element hash_multimap, który ma klucz równoważne z określonym kluczem.  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz do dopasowania za pomocą klucza sortowania z elementem z hash_multimap przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator, którego dotyczy lokalizację pierwszy element z określonym kluczem lub lokalizacji pomyślne ostatnim elementem w hash_multimap, jeśli nie znaleziono klucza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwracającą iterator, którego dotyczy element hash_multimap, którego klucz sortowania jest **równoważne** do argumentu klucz w obszarze binarny predykatu wywołujące kolejność oparty na mniej niż porównywalności relacji.  
  
 Jeśli wartość zwracana **znaleźć** jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, można zmodyfikować obiektu hash_multimap.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_find.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(3, 20));  
    hm1.insert(Int_Pair(3, 30));  
  
    hm1_RcIter = hm1.find(2);  
    cout << "The element of hash_multimap hm1 with a key of 2 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    hm1_RcIter = hm1.find(3);  
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    // If no match is found for the key, end() is returned  
    hm1_RcIter = hm1.find(4);  
  
    if (hm1_RcIter == hm1.end())  
        cout << "The hash_multimap hm1 doesn't have an element "  
             << "with a key of 4." << endl;  
    else  
        cout << "The element of hash_multimap hm1 with a key of 4 is: "  
             << hm1_RcIter -> second << "." << endl;  
  
    // The element at a specific location in the hash_multimap can be  
    // found using a dereferenced iterator addressing the location  
    hm1_AcIter = hm1.end();  
    hm1_AcIter--;  
    hm1_RcIter = hm1.find(hm1_AcIter -> first);  
    cout << "The first element of hm1 with a key matching"  
         << endl << "that of the last element is: "  
         << hm1_RcIter -> second << "." << endl;  
  
    // Note that the first element with a key equal to  
    // the key of the last element is not the last element  
    if (hm1_RcIter == --hm1.end())  
        cout << "This is the last element of hash_multimap hm1."  
             << endl;  
    else  
        cout << "This is not the last element of hash_multimap hm1."  
             << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="get_allocator"></a>  hash_multimap::get_allocator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca kopię obiektu alokatora użyta do skonstruowania hash_multimap.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy hash_multimap Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int>::allocator_type hm1_Alloc;  
   hash_multimap <int, int>::allocator_type hm2_Alloc;  
   hash_multimap <int, double>::allocator_type hm3_Alloc;  
   hash_multimap <int, int>::allocator_type hm4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> hm2;  
   hash_multimap <int, double> hm3;  
  
   hm1_Alloc = hm1.get_allocator( );  
   hm2_Alloc = hm2.get_allocator( );  
   hm3_Alloc = hm3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm3.max_size( ) <<  "." << endl;  
  
   // The following line creates a hash_multimap hm4  
   // with the allocator of hash_multimap hm1.  
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );  
  
   hm4_Alloc = hm4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hm1_Alloc == hm4_Alloc )     
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
  
##  <a name="hash_multimap"></a>  hash_multimap::hash_multimap  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Tworzy hash_multimap, który jest pusta lub kopii całości lub części innych hash_multimap —.  
  
```  
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,  
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp);

 
hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp,  
    const Allocator& Al);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu hash_multimap, która domyślnie określa `Allocator`.|  
|`Comp`|Funkcja porównywania typu `const Traits` porządkowania elementów w tablicy, która domyślnie określa `Traits`.|  
|`Right`|Mapy skonstruowane zestawu ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Initializer_list do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Typ obiektu przydzielania, który zarządza przechowywania w pamięci dla hash_multimap i który później może być zwracany przez wywołanie metody przechowywania wszystkie konstruktory [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra są używane do zastąpienia alternatywnych allocators —.  
  
 Wszystkie konstruktory zainicjować ich hash_multimap.  
  
 Wszystkie konstruktory przechowywania obiektem funkcji typu `Traits` który jest używany do ustanawiania zamówienia wśród kluczy hash_multimap i później może być zwracany przez wywołanie metody [key_comp](#key_comp).  
  
 Pierwsze trzy konstruktorów Określ pusty hash_multimap początkowej; drugi określa typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów i trzeci jawnie określa typ alokatora ( `_Al`) do użycia. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.  
  
 Konstruktor czwarty Określa kopię hash_multimap `Right`.  
  
 Konstruktory trzech kolejnych skopiuj zakres `First, Last)` mapy rosnącymi explicitness określania typu porównanie funkcji klasy **cech** i przydzielania.  
  
 Konstruktor ósmego przenosi hash_multimap `Right`.  
  
 Końcowe konstruktorów trzech użyć initializer_list.  
  
##  <a name="insert"></a>  hash_multimap::INSERT  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Wstawia element lub zakres elementów do hash_multimap.  
  
```  
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,  
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

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
|`Val`|Wartość elementu ma zostać wstawiony do hash_multimap, o ile nie zawiera już ten element lub ogólnie rzecz biorąc, chyba że jest on już zawiera element, którego klucz ekwiwalentnie porządkowania.|  
|`Where`|Wskazówka o miejscu rozpocząć wyszukiwanie poprawny punkt wstawiania.|  
|`First`|Pozycja pierwszego elementu do skopiowania z mapy.|  
|`Last`|Pozycja poza ostatni element do skopiowania z mapy.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsze dwie `insert` Członkowskie zwracają iterację, który wskazuje miejsce, w którym dodano nowego elementu.  
  
 Trzeci funkcji członkowskiej używa initializer_list dla elementów do wstawienia.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wartości elementów do mapy odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)` w określonym zestawie.  
  
 Ostatnie dwa `insert` funkcje Członkowskie działają tak samo, jak dwa pierwsze z tą różnicą, że ich przenoszenia — konstrukcja wstawiona wartość.  
  
### <a name="remarks"></a>Uwagi  
 [Value_type](#value_type) elementu jest parę, tak, aby wartość elementu parę uporządkowanych, w którym znajduje się pierwszy składnik jest równa wartości klucza i drugi składnik jest równa wartości danych elementu.  
  
 Wstawiania może wystąpić podczas amortyzowanego stałej wskazówka dotycząca wersji `insert`, zamiast logarytmicznej czasu, gdy punkt wstawiania poniższą `Where`.  
  
##  <a name="iterator"></a>  hash_multimap::iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w hash_multimap.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 **Iterator** zdefiniowany przez punkty hash_multimap do obiektów [value_type](#value_type), są typu `pair` \< **const klucza, typ**>, której pierwszy element członkowski ma kluczowe znaczenie dla elementu i sekundę, których element członkowski jest mapowanych elementu danych przez element.  
  
 Aby usunąć odwołania do **iterator** `Iter` wskazuje element hash_multimap, użyj  **->**  operatora.  
  
 Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter`  ->  **pierwszy**, który jest odpowiednikiem (\* `Iter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `Iter`  ->  **drugi**, który jest odpowiednikiem (\* `Iter`). **pierwszy**.  
  
 Typ **iterator** może służyć do modyfikowania wartości elementu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.  
  
##  <a name="key_comp"></a>  hash_multimap::key_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Pobiera kopię porównania obiekt używany do kolejność kluczy w hash_multimap.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcja hash_multimap używa do porządkowania jej elementów.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt przechowywanych definiuje funkcję elementu członkowskiego  
  
 **bool — operator (const klucza &** `left` **, klucz const &** `right` **);**  
  
 która zwraca **true** Jeśli `left` poprzedza i nie jest równa `right` w kolejności sortowania.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_key_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;  
   hash_multimap <int, int, hash_compare<int, less<int>>   
      >::key_compare kc1 = hm1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
  
   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;  
   hash_multimap <int, int, hash_compare<int, greater<int>>   
      >::key_compare kc2 = hm2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>  hash_multimap::key_compare  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w hash_multimap.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 **key_compare** jest synonimem parametru szablonu `Traits`.  
  
 Aby uzyskać więcej informacji na temat `Traits` zobacz [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="key_type"></a>  hash_multimap::key_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który opisuje obiektu klucza sortowania stanowi każdy element hash_multimap.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `key_type` synonim parametru szablonu jest `Key`.  
  
 Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_compare`.  
  
##  <a name="lower_bound"></a>  hash_multimap::lower_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca pierwszy element w hash_multimap — iteratora klucz, który jest równy lub większy niż określony klucz.  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multimap przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Iterator](#iterator) lub [const_iterator](#const_iterator) który adresy lokalizacji elementu w hash_multimap za pomocą klucza, która jest równa lub większa niż klucz argumentu, lub które adresów lokalizacji pomyślne wykonanie ostatniego Element hash_multimap, jeśli nie znaleziono klucza.  
  
 Jeśli wartość zwracana `lower_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `lower_bound` jest przypisany do **iterator**, można zmodyfikować obiektu hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter,   
      hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.lower_bound( 2 );  
   cout << "The element of hash_multimap hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.lower_bound( 3 );  
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key matching"  
        << endl << " that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // Note that the first element with a key equal to  
   // the key of the last element is not the last element  
   if ( hm1_RcIter == --hm1.end( ) )  
      cout << "This is the last element of hash_multimap hm1."  
           << endl;  
   else  
      cout << "This is not the last element of hash_multimap hm1."  
           << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
 that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="mapped_type"></a>  hash_multimap::mapped_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który reprezentuje typ danych przechowywanych w hash_multimap.  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `mapped_type` synonim parametru szablonu jest `Type`.  
  
 Aby uzyskać więcej informacji na temat `Type` zobacz [hash_multimap — klasa](../standard-library/hash-multimap-class.md) tematu.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.  
  
##  <a name="max_size"></a>  hash_multimap::max_size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca maksymalną długość hash_multimap.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_max_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: size_type i;  
  
   i = hm1.max_size( );  
   cout << "The maximum possible length "  
        << "of the hash_multimap is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>  hash_multimap::operator =  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zamienia elementy hash_multimap kopię hash_multimap innego.  
  
```  
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|[Hash_multimap](../standard-library/hash-multimap-class.md) kopiowane do `hash_multimap`.|  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu elementy w `hash_multimap`, `operator=` albo kopiuje lub przenosi zawartość `right` do `hash_multimap`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_operator_as.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> v1, v2, v3;  
   hash_multimap<int, int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>  hash_multimap::Pointer  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który dostarcza wskaźnik do elementu hash_multimap.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu.  
  
 W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie hash_multimap.  
  
   
  
##  <a name="rbegin"></a>  hash_multimap::rbegin  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca iteratora adresowania pierwszym elementem w hash_multimap odwróconej.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego adresowania pierwszym elementem w odwróconej hash_multimap lub adresowania co była ostatnim elementem w hash_multimap stałe.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z odwróconej hash_multimap — podobnie jak [rozpocząć](#begin) jest używany z hash_multimap.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, a następnie nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu hash_multimap.  
  
 `rbegin` może służyć do iterowania po hash_multimap Wstecz.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_rbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = hm1.rbegin( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "After the erasure, the first element"  
        << "\n in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the first element  
 in the reversed hash_multimap is 2.  
```  
  
##  <a name="reference"></a>  hash_multimap::Reference  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który zawiera odwołanie do elementu przechowywane w hash_multimap.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_reference.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of first element in the hash_multimap is "  
        << Ref2 << "." << endl;  
  
   //The non-const_reference can be used to modify the   
   //data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>  hash_multimap::rend  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multimap iteratora.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej hash_multimap (lokalizacja miał przed pierwszym elementem w stałe hash_multimap).  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z odwróconej hash_multimap — podobnie jak [zakończenia](#end) jest używany z hash_multimap.  
  
 Jeśli wartość zwracana `rend` jest przypisany do [const_reverse_iterator](#const_reverse_iterator), a następnie nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `rend` jest przypisany do [reverse_iterator](#reverse_iterator), a następnie można zmodyfikować obiektu hash_multimap.  
  
 `rend` można sprawdzać, czy osiągnął koniec jego hash_multimap odwrotnej iteratora.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_rend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = --hm1.rend( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 1.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the last element in the reversed hash_multimap is 2.  
```  
  
##  <a name="reverse_iterator"></a>  hash_multimap::reverse_iterator  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej hash_multimap.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` jest używany do iterowania po hash_multimap — odwrotnie.  
  
 `reverse_iterator` Zdefiniowany przez punkty hash_multimap do obiektów [value_type](#value_type), które są typu `pair` \< **const klucza, wpisz**>. Wartość klucza jest dostępna za pośrednictwem pierwszego pary elementu członkowskiego i wartość mapowanego elementu jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.  
  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.  
  
##  <a name="size"></a>  hash_multimap::size  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca liczbę elementów w hash_multimap.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano użycie funkcji członkowskiej hash_multimap::size.  
  
```  
// hash_multimap_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    i = hm1.size();  
    cout << "The hash_multimap length is " << i << "." << endl;  
  
    hm1.insert(Int_Pair(2, 4));  
    i = hm1.size();  
    cout << "The hash_multimap length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_multimap length is 1.  
The hash_multimap length is now 2.  
```  
  
##  <a name="size_type"></a>  hash_multimap::size_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ liczby całkowitej bez znaku, które zlicza liczbę elementów w hash_multimap.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`  
  
##  <a name="swap"></a>  hash_multimap::swap  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zamienia hash_multimaps dwa elementy.  
  
```  
void swap(hash_multimap& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_multimap dostarczanie elementy zamianę lub hash_multimap, której elementy są wymienianych z tymi hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch hash_multimaps, której elementy są wymieniane.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_swap.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2, hm3;  
   hash_multimap <int, int>::iterator hm1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm2.insert ( Int_Pair ( 10, 100 ) );  
   hm2.insert ( Int_Pair ( 20, 200 ) );  
   hm3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hm1.swap( hm2 );  
  
   cout << "After swapping with hm2, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hm1, hm3 );  
  
   cout << "After swapping with hm3, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_multimap hm1 is: 10 20 30.  
After swapping with hm2, hash_multimap hm1 is: 100 200.  
After swapping with hm3, hash_multimap hm1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  hash_multimap::upper_bound  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zwraca pierwszy element w hash_multimap iteratora klucz, który jest większy niż określony klucz.  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z hash_multimap przeszukiwany.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Iterator](#iterator) lub [const_iterator](#const_iterator) który adresy lokalizacji elementu w hash_multimap za pomocą klucza jest większa niż klucz argumentu, lub że adresów lokalizacji pomyślne wykonanie ostatniego elementu w hash_multimap — Jeśli nie znaleziono klucza.  
  
 Jeśli wartość zwracana `upper_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu hash_multimap. Jeśli wartość zwracana `upper_bound` jest przypisany do **iterator**, można zmodyfikować obiektu hash_multimap.  
  
### <a name="remarks"></a>Uwagi  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm1.insert ( Int_Pair ( 3, 40 ) );  
  
   hm1_RcIter = hm1.upper_bound( 1 );  
   cout << "The 1st element of hash_multimap hm1 with "  
        << "a key greater than 1 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.upper_bound( 2 );  
   cout << "The first element of hash_multimap hm1\n with a key "  
        << " greater than 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.begin( );  
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key greater than"  
        << endl << " that of the initial element of hm1 is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.  
The first element of hash_multimap hm1  
 with a key  greater than 2 is: 30.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key greater than  
 that of the initial element of hm1 is: 20.  
```  
  
##  <a name="value_comp"></a>  hash_multimap::value_comp  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów hash_multimap porównując wartości klucza.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt funkcja porównania hash_multimap używa do porządkowania jej elementów.  
  
### <a name="remarks"></a>Uwagi  
 Dla hash_multimap *m*, jeśli dwa elementy *e*1 ( *k*1 *, d*1) i *e*2 ( *k*2 *, d*2) obiekty typu [value_type](#value_type), gdzie *k*1 i *k*2 są ich kluczy typu [key_type](#key_type) i `d`1 i `d`2 są dane typu [mapped_type](#mapped_type), następnie *m.*`value_comp`() ( *e*1 *, e*2) jest odpowiednikiem *m.*`key_comp`() ( *k*1 *, k*2). Obiekt przechowywanych definiuje funkcję elementu członkowskiego  
  
 **bool operator**( **value_type &**`left`, **value_type &** `right`);  
  
 która zwraca **true** Jeśli wartość klucza `left` poprzedza i nie jest równa wartości klucza `right` w kolejności sortowania.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_value_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;  
   hash_multimap <int, int, hash_compare<int, less<int>>   
      >::value_compare vc1 = hm1.value_comp( );  
   hash_multimap <int,int>::iterator Iter1, Iter2;  
  
   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *Iter1, *Iter2 ) == true )  
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does "  
           << "not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if( vc1( *Iter2, *Iter1 ) == true )     
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does "  
           << "not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_type"></a>  hash_multimap::value_type  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Typ, który reprezentuje typ obiektu przechowywanego w hash_multimap.  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `value_type` został zadeklarowany jako pary\<const [key_type](#key_type), [mapped_type](#mapped_type)> i nie Sparuj\<key_type, mapped_type >, ponieważ nie można zmieniać klucze asocjacyjnej kontenera za pomocą nieunikatowego iteratora lub odwołanie.  
  
   
  
### <a name="example"></a>Przykład  
  
```cpp  
// hash_multimap_value_type.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: key_type key1;  
   hash_multimap <int, int> :: mapped_type mapped1;  
   hash_multimap <int, int> :: value_type value1;  
   hash_multimap <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare another way to insert objects into a hash_multimap  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
  
   // Initializing key1 and mapped1  
   key1 = ( hm1.begin( ) -> first );  
   mapped1 = ( hm1.begin( ) -> second );  
  
   cout << "The key of first element in the hash_multimap is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the hash_multimap is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The keys of the mapped elements are: 1 2.  
The values of the mapped elements are: 10 20.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

