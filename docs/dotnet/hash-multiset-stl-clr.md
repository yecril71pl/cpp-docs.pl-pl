---
title: hash_multiset — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 71ae758f969c03ecfd6d14721208a2a496309ec0
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376329"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)
Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającego dostęp dwukierunkowy. Korzystasz z kontenera `hash_multiset` każdego wpisu tabeli przechowywania dwukierunkowy, aby zarządzać sekwencję elementów w postaci tabeli wyznaczania wartości skrótu, połączoną listę węzłów i w każdym węźle przechowywania jeden element. Wartość każdy element służy jako klucz do ustalania kolejności sekwencji.  
  
 W poniższym opisie `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak *klucz* o ile nie jest typem odwołania, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Key>  
    ref class hash_multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Key*  
 Typ kluczowy składnik elementu w kontrolowanej sekwencji.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext — / hash_set >  
  
 **Namespace:** cliext —  
  
## <a name="declarations"></a>Deklaracje  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|  
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|  
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie odległości ze znakiem) między dwoma elementami.|  
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla kontenera.|  
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólny interfejs dla kontenera.|  
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla ogólny interfejs dla kontenera.|  
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólny interfejs dla kontenera.|  
|[hash_multiset::hasher (STL/CLR)](#hasher)|Delegat wyznaczania wartości skrótu dla klucza.|  
|[hash_multiset::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|  
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|Szeregowania delegat dla obiektu dwa klucze.|  
|[hash_multiset::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|  
|[hash_multiset::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|  
|[hash_multiset::size_type (STL/CLR)](#size_type)|Typ odległości (wartość nieujemną) między dwoma elementami.|  
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|Szeregowania delegat dla obiektu dwie wartości elementów.|  
|[hash_multiset::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[hash_multiset::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|  
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|Zlicza liczbę przedziałów.|  
|[hash_multiset::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|  
|[hash_multiset::count (STL/CLR)](#count)|Liczba elementów pasujących do określonego klucza.|  
|[hash_multiset::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[hash_multiset::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|  
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[hash_multiset::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|  
|[hash_multiset::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|Kopiuje delegata wyznaczania wartości skrótu dla klucza.|  
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|Konstruuje obiekt kontenera.|  
|[hash_multiset::insert (STL/CLR)](#insert)|Dodaje elementy.|  
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|Kopiuje szeregowania delegata dwa klucze.|  
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|Oblicza średnią liczbę elementów na przedział.|  
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|  
|[hash_multiset::make_value (STL/CLR)](#make_value)|Tworzy obiekt wartości.|  
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|  
|[hash_multiset::rehash (STL/CLR)](#rehash)|Przebudowuje tabelę mieszania.|  
|[hash_multiset::rend (STL/CLR)](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|  
|[hash_multiset::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[hash_multiset::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|  
|[hash_multiset::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|  
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|Kopiuje szeregowania delegata dwie wartości elementów.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[hash_multiset::operator= (STL/CLR)](#op)|Zastępuje kontrolowanej sekwencji.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplikowanie obiektów.|  
|<xref:System.Collections.IEnumerable>|Przeprowadzaj sekwencjonowanie przez elementy.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Przeprowadzaj Sekwencjonowanie za pośrednictwem typizowanych elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy typizowanych elementów.|  
|IHash\<klucz, wartość >|Obsługa kontenerów ogólnego.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia pamięć dla sekwencji, które kontroluje jako poszczególnych węzłów w połączonej listy dwukierunkowej. Aby przyspieszyć dostęp, obiekt przechowuje różnej długości tablicy wskaźników do listy (Tabela skrótów), efektywne zarządzanie całą listę jako sekwencja podlisty, lub przedziałów. Wstawia elementy do zasobnika, który utrzymuje uporządkowanym, zmieniając linki między węzłami, nigdy, kopiując zawartość jednego węzła do drugiego. Oznacza to, można wstawić i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.  
  
 Obiekt porządkuje każdego przedziału, którą kontroluje, przez wywołanie obiektu przechowywanej delegat typu [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli obiekt delegowany nie zostanie określony, wartością domyślną jest porównanie `operator<=(key_type, key_type)`.  
  
 Dostęp do obiektu delegowanego przechowywanych przez wywołanie funkcji elementu członkowskiego [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Obiektu delegowanego musi definiować równoważną kolejność pomiędzy kluczami typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Oznacza to, dla dowolnego dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)` Zwraca wynik tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y) && key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważną kolejność.  
  
 Szeregowania reguł, który zachowuje się jak `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` lub `operator==(key_type, key_type)` definiuje kolejność eqivalent.  
  
 Należy pamiętać, że kontener gwarantuje tylko elementy którego klucze mają równoważną kolejność (i skrótu na tę samą wartość liczby całkowitej) sąsiadująco w pojemniku. W odróżnieniu od klasy szablonu [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md), obiekt klasy szablonu `hash_multiset` nie wymaga ona, że klucze dla wszystkich elementów są unikatowe. (Dwa lub więcej klucze mają równoważną kolejność.)  
  
 Obiektu określa, w którym zasobniku powinien zawierać danego klucza sortowania przez wywołanie obiektu przechowywanej delegat typu [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Ten przechowywany obiekt jest dostępu przez wywołanie funkcji elementu członkowskiego [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` można uzyskać wartość całkowitą, która jest zależna od wartości klucza. Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli żaden obiekt delegowany jest określony, wartość domyślna to funkcja `System::Object::hash_value(key_type)`. Oznacza to, do żadnych kluczy `X` i `Y`:  
  
 `hash_delegate()(X)` zwraca ten sam wynik liczby całkowitej na każde wywołanie.  
  
 Jeśli `X` i `Y` mają równoważną kolejność, następnie `hash_delegate()(X)` powinna zwracać ten sam wynik liczby całkowitej jako `hash_delegate()(Y)`.  
  
 Każdy element służy jako zarówno klucz i wartość. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwania, wstawiania i usuwania dowolnego elementu z liczba operacji, która jest niezależna od liczbę elementów w sekwencji (stały czas) — co najmniej w najlepszym przypadku. Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Jeśli wartości skrótu nie są równomiernie rozłożone, jednak tabeli mieszania może dwa wymiary degeneracji. W skrajnej — dla funkcji skrótu, która zawsze zwraca taką samą wartość — wyszukiwania, wstawiania i usuwania są proporcjonalne do liczby elementów w sekwencji (liniowy czas). Kontener usiłują wybierz funkcję mieszania uzasadnione, mean zasobnika rozmiar, a rozmiar tabeli skrótów (całkowita liczba zasobników), ale można zastąpić niektóre lub wszystkie z tych opcji. Zobacz na przykład funkcje [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) i [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_multiset — obsługują Iteratory dwukierunkowe, co oznacza, że użytkownik może przechodzić do sąsiadujących elementów podany iterator, który wskazuje element w kontrolowanej sekwencji. Specjalne węzłem odnosi się do iteratora zwrócony przez [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Można zmniejszyć tego iteratora, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Inkrementacji iteratora hash_multiset, aby dotrzeć do węzła głównego, a następnie porównaj równa `end()`. Ale nie można wyłuskać iteratora zwrócony przez `end()`.  
  
 Należy pamiętać, że nie można odwołać się do elementu hash_multiset bezpośrednio podanej pozycji liczbowych — wymagającego iteratora dostępu swobodnego.  
  
 Hash_multiset iterator przechowuje dojścia do węzła skojarzone hash_multiset, która z kolei przechowuje dojście do jego skojarzony kontener. Iteratory można użyć tylko w nich obiekty skojarzony kontener. Hash_multiset iterator zachowuje ważność tak długo, jak jego hash_multiset skojarzony węzeł jest skojarzony z niektórych hash_multiset. Ponadto, prawidłowy iteratora jest wyłuskiwania — służy do uzyskiwania dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor do jego przechowywanej wartości. Niszczenie kontenera usuwa wszystkie elementy. W związku z tym kontener, którego typ elementu jest klasą ref gwarantuje, że żadne elementy on nakreślał kontenera. Należy jednak pamiętać, że kontener dojścia nie *nie* zniszczyć jego elementów.  
  
## <a name="members"></a>Elementy członkowskie

## <a name="begin"></a> hash_multiset::BEGIN (STL/CLR)
Określa początek kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca iteratora dwukierunkowego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_begin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="bucket_count"></a> hash_multiset::bucket_count (STL/CLR)
Zlicza liczbę przedziałów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
int bucket_count();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcje elementów członkowskich zwraca bieżącej liczby przedziałów. Możesz użyć do określenia rozmiaru tablicy skrótów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_bucket_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="clear"></a> hash_multiset::Clear (STL/CLR)
Usuwa wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego skutecznie wywołuje [hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md) `(` [hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md) `(),` [hash_multiset::end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a> hash_multiset::const_iterator (STL/CLR)
Typ iteratora stałego dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt nieokreślonego typu `T2` który może służyć jako iterator dwukierunkowy stałe dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> hash_multiset::const_reference (STL/CLR)
Typ stałego odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje stałe odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_multiset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> hash_multiset::const_reverse_iterator (STL/CLR)
Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji...  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt nieokreślonego typu `T4` który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="count"></a> hash_multiset::Count (STL/CLR)
Wyszukuje liczbę elementów pasujących do określonego klucza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski funkcji zwraca liczbę elementów w kontrolowanej sekwencji, które mają równoważną kolejność z *klucz*. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  
  
## <a name="difference_type"></a> hash_multiset::difference_type (STL/CLR)
Typy odległości ze znakiem między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczba element prawdopodobnie ujemna.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::difference_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> hash_multiset::EMPTY (STL/CLR)
Sprawdza, czy nie ma żadnych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy hash_multiset jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_empty.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> hash_multiset::end (STL/CLR)
Określa koniec kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca iterator dwukierunkowy, który wskazuje tuż za koniec kontrolowanej sekwencji. Służy do uzyskiwania iterator, który określa koniec kontrolowanej sekwencji; jego stan nie zmieniać, jeśli zmieni się długość kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_end.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_multiset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  
  
## <a name="equal_range"></a> hash_multiset::equal_range (STL/CLR)
Wyszukuje zakres, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca parę iteratorów `cliext::pair<iterator, iterator>(` [hash_multiset::lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md) `(key),` [hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`. Możesz użyć do określenia zakresu elementów aktualnie w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
typedef Myhash_multiset::pair_iter_iter Pairii;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
```  

## <a name="erase"></a> hash_multiset::ERASE (STL/CLR)
Usuwa elementy z określonych pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parametry  
 *pierwszy*  
 Początek zakresu, aby wymazać.  
  
 *Klucz*  
 Wartość klucza do wymazania.  
  
 *ostatni*  
 Koniec zakresu, aby wymazać.  
  
 *gdzie*  
 Element, aby wymazać.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji wskazywany przez *gdzie*i zwraca iterator opisujący pierwszy element pozostający poza elementem, który został usunięty, lub [hash_multiset::end () STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()` jeśli taki element nie istnieje. Umożliwia ona usunąć pojedynczy element.  
  
 Funkcja drugiego członka usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`) i zwraca iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub `end()` jeśli taki element nie istnieje... Umożliwia ona usunąć zero lub więcej elementów sąsiadujących.  
  
 Trzecia funkcja członkowska usuwa jakiegokolwiek elementu w kontrolowanej sekwencji, których klucz ma równoważną kolejność do *klucz*i zwraca liczbę elementów usuniętych. Możesz użyć do usunięcia, a liczba wszystkich elementów, które odpowiadają określonemu kluczowi.  
  
 Każdy element wymazywania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  

## <a name="find"></a> hash_multiset::Find (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli co najmniej jednego elementu w kontrolowanej sekwencji ma równoważną kolejność z *klucz*, funkcja elementu członkowskiego zwraca iterację, wyznaczanie jednego z tych elementów; w przeciwnym razie zwraca [hash_multiset::end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`()`. Umożliwia ona obecnie Znajdź element w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_find.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
``` 

## <a name="generic_container"></a> hash_multiset::generic_container (STL/CLR)
Typ ogólny interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IHash<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje ogólny interfejs dla tej klasy szablonu w kontenerze.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_generic_container.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
   
## <a name="generic_iterator"></a> hash_multiset::generic_iterator (STL/CLR)
Typ iteratora do użytku z ogólny interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje iterator ogólny, który mogą być używane z ogólny interfejs dla tej klasy szablonu w kontenerze.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="generic_reverse_iterator"></a> hash_multiset::generic_reverse_iterator (STL/CLR)
Typ iteratora odwrotnego do użytku z ogólny interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje iterator odwrotny ogólnego, które mogą być używane z ogólny interfejs dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> hash_multiset::generic_value (STL/CLR)
Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="hash_delegate"></a> hash_multiset::hash_delegate (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
hasher^ hash_delegate();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca delegata używany do konwersji wartości klucza na liczbę całkowitą. Możesz użyć do tworzenia skrótu klucza.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="hash_multiset"></a> hash_multiset::hash_multiset (STL/CLR)
Konstruuje obiekt kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pierwszy*  
 Początek zakresu do wstawienia.  
  
 *hashfn*  
 Hash — funkcja klucze mapowania do zasobników.  
  
 *ostatni*  
 Koniec zakresu do wstawienia.  
  
 *P.*  
 Kolejność predykat dla kontrolowanej sekwencji.  
  
 *right*  
 Obiekt lub zakresu do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `hash_multiset();`  
  
 Inicjuje kontrolowanej sekwencji bez elementów z domyślną kolejność predykatu `key_compare()`i za pomocą domyślnej funkcji skrótu. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji bez elementów, z predykatem szeregowania *pred*i za pomocą domyślnej funkcji skrótu. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, określony predykat szeregowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji bez elementów, z predykatem szeregowania *pred*i za pomocą funkcji skrótu *hashfn*. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, za pomocą określonego szeregowania funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right.begin()`, `right.end()`) przy użyciu domyślnego porządkowanie predykat i za pomocą domyślnej funkcji skrótu. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt hash_multiset *prawo*z predykatem, po którym sortowania domyślnego i funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right->begin()`, `right->end()`) przy użyciu domyślnego porządkowanie predykat i za pomocą domyślnej funkcji skrótu. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt hash_multiset *prawo*z predykatem, po którym sortowania domyślnego i funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`) przy użyciu domyślnego porządkowanie predykat i za pomocą domyślnej funkcji skrótu. Umożliwia ona Utwórz kopię innej sekwencji kontrolowanej sekwencji z domyślną kolejność funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), z predykatem szeregowania *pred*i za pomocą domyślnej funkcji skrótu. Umożliwia ona kopię sekwencji kontrolowanej innej sekwencji, określony predykat szeregowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), z predykatem szeregowania *pred*i za pomocą funkcji skrótu *hashfn*. Umożliwia ona kopię sekwencji kontrolowanej sekwencji innego, określonego szeregowania funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*z domyślną kolejność predykat i za pomocą domyślnej funkcji skrótu. Umożliwia ona kopię sekwencji kontrolowanej innej sekwencji opisanego przez moduł wyliczający z domyślną kolejność funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, z predykatem szeregowania *pred*i za pomocą domyślnej funkcji skrótu. Umożliwia ona kopię sekwencji kontrolowanej innej sekwencji opisanego przez moduł wyliczający, przy użyciu określonego szeregowania predykat i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, z predykatem szeregowania *pred*i za pomocą funkcji skrótu *hashfn*. Umożliwia ona kopię sekwencji kontrolowanej innej sekwencji opisanego przez moduł wyliczający, za pomocą określonego szeregowania funkcji predykatu i wyznaczania wartości skrótu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  

## <a name="hasher"></a> hash_multiset::hasher (STL/CLR)
Delegat wyznaczania wartości skrótu dla klucza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt delegowany, który konwertuje wartość klucza na liczbę całkowitą.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  

## <a name="insert"></a> hash_multiset::INSERT (STL/CLR)
Dodaje elementy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pierwszy*  
 Początek zakresu do wstawienia.  
  
 *ostatni*  
 Koniec zakresu do wstawienia.  
  
 *right*  
 Wyliczenie do wstawienia.  
  
 *Val*  
 Wartość klucza do wstawienia.  
  
 *gdzie*  
 Miejsce w kontenerze, aby wstawić (tylko wskazówki).  
  
### <a name="remarks"></a>Uwagi  
 Każda z tych funkcji elementu członkowskiego wstawia sekwencję określone przez pozostałe argumenty operacji.  
  
 Pierwsza funkcja elementu członkowskiego wstawia element z wartością *val*i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona wstawić jeden element.  
  
 Funkcja drugiego członka wstawia element z wartością *val*przy użyciu *gdzie* jako wskazówkę (Aby poprawić wydajność) i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona Wstaw pojedynczy element, który może być w przylegającymi do elementu, które znasz.  
  
 Trzecia funkcja członkowska wstawia sekwencję [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów, skopiowane z innej sekwencji.  
  
 Czwarty funkcja elementu członkowskiego wstawia sekwencję wyznaczonym przez *prawo*. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Każdy element wstawiania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawiania może wystąpić w amortyzowanym stałym czasie, jednak podane wskazówkę, opisująca element przylegające do punktu wstawiania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  

## <a name="iterator"></a> hash_multiset::iterator (STL/CLR)
Typ iteratora dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator dwukierunkowy dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_hash_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> hash_multiset::key_comp (STL/CLR)
Kopiuje szeregowania delegata dwa klucze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwa klucze.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> hash_multiset::key_compare (STL/CLR)
Szeregowania delegat dla obiektu dwa klucze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla delegata, która określa kolejność argumentów klucza.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_type"></a> hash_multiset::key_type (STL/CLR)
Typ klucza sortowania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla parametru szablonu *klucz*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_multiset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="load_factor"></a> hash_multiset::load_factor (STL/CLR)
Oblicza średnią liczbę elementów na przedział.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
float load_factor();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca `(float)` [hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md) `() /` [hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`. Możesz użyć do określenia rozmiaru przedziału średniej.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="lower_bound"></a> hash_multiset::lower_bound (STL/CLR)
Znajduje początek zakresu, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego Określa pierwszy element `X` w kontrolowanej sekwencji, która tworzy skrót do tego samego zasobnika jako *klucz* i ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje, zwraca [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza `X`. Umożliwia ona obecnie zlokalizuj na początku sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> hash_multiset::make_value (STL/CLR)
Tworzy obiekt wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do użycia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca `value_type` obiektu, którego klucz jest *klucz*. Możesz użyć do redagowania odpowiedni do użytku z wielu innych funkcji Członkowskich obiektu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  
  
## <a name="max_load_factor"></a> hash_multiset::max_load_factor (STL/CLR)
Pobiera lub ustawia maksymalną liczbę elementów na przedział.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### <a name="parameters"></a>Parametry  
 *new_factor*  
 Maksymalna nowe obciążenia współczynnik do przechowywania.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza funkcja elementu członkowskiego zwraca bieżący współczynnik przechowywanych maksymalnego obciążenia. Możesz użyć do określenia rozmiar maksymalny przedział średniej.  
  
 Funkcja drugiego członka zastępuje współczynnik maksymalnego obciążenia magazynu za pomocą *new_factor*. Nie automatycznego rehashing występuje aż do kolejnych insert.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="op"></a> hash_multiset::operator = (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Kontener do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> hash_multiset::rbegin (STL/CLR)
Określa początek kontrolowanej sekwencji odwróconej.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wyznacza wartość ostatniego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Dzięki temu wyznacza `beginning` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  

## <a name="reference"></a> hash_multiset::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_multiset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
``` 

## <a name="rehash"></a> hash_multiset::rehash (STL/CLR)
Przebudowuje tabelę mieszania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void rehash();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego przebudowuje tabelę mieszania, upewniając się, że [hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md) `() <=` [hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md). W przeciwnym razie tabeli mieszania rozmiar zwiększa się tylko w razie potrzeby po wstawieniu. (Nigdy automatycznie zmniejszenie rozmiaru.) Umożliwia ona Dopasowywanie rozmiaru tablicy skrótów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="rend"></a> hash_multiset::rend (STL/CLR)
Określa koniec kontrolowanej sekwencji odwróconej.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wskazuje tuż za początek kontrolowanej sekwencji. Dzięki temu wyznacza `end` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_rend.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```  

## <a name="reverse_iterator"></a> hash_multiset::reverse_iterator (STL/CLR)
Typ iteratora odwrotnego dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt nieokreślonego typu `T3` który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="size"></a> hash_multiset::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> hash_multiset::size_type (STL/CLR)
Typ odległości ze znakiem między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczby nieujemnej wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::size_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="swap"></a> hash_multiset::swap (STL/CLR)
Zamienia zawartości dwóch kontenerów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void swap(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Kontener do wymiany zawartości z.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `this` i *prawo*. Robi to w stałym czasie i w wyniku weryfikacji zgłasza wyjątek bez wyjątków. Możesz użyć go w prosty sposób do wymiany zawartości dwóch kontenerów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_multiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
d e f  
d e f  
a b c  
```    

## <a name="to_array"></a> hash_multiset::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="upper_bound"></a> hash_multiset::upper_bound (STL/CLR)
Znajduje koniec zakresu, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego określa po ostatnim elemencie `X` w kontrolowanej sekwencji, która tworzy skrót do tego samego zasobnika jako *klucz* i ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, funkcja zwraca [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza pierwszego elementu poza `X`. Umożliwia ona obecnie Znajdź koniec sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  

## <a name="value_comp"></a> hash_multiset::value_comp (STL/CLR)
Kopiuje szeregowania delegata dwie wartości elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwie wartości elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> hash_multiset::value_compare (STL/CLR)
Szeregowania delegat dla obiektu dwie wartości elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla delegata, który określa kolejność wartości argumentów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> hash_multiset::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla `generic_value`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_multiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  