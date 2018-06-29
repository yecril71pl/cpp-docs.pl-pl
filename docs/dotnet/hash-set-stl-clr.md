---
title: hash_set — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set
- cliext::hash_set::begin
- cliext::hash_set::bucket_count
- cliext::hash_set::clear
- cliext::hash_set::const_iterator
- cliext::hash_set::const_reference
- cliext::hash_set::const_reverse_iterator
- cliext::hash_set::count
- cliext::hash_set::difference_type
- cliext::hash_set::empty
- cliext::hash_set::end
- cliext::hash_set::equal_range
- cliext::hash_set::erase
- cliext::hash_set::find
- cliext::hash_set::generic_container
- cliext::hash_set::generic_iterator
- cliext::hash_set::generic_reverse_iterator
- cliext::hash_set::generic_value
- cliext::hash_set::hash_delegate
- cliext::hash_set::hash_set
- cliext::hash_set::hasher
- cliext::hash_set::insert
- cliext::hash_set::iterator
- cliext::hash_set::key_comp
- cliext::hash_set::key_compare
- cliext::hash_set::key_type
- cliext::hash_set::load_factor
- cliext::hash_set::lower_bound
- cliext::hash_set::make_value
- cliext::hash_set::max_load_factor
- cliext::hash_set::operator=
- cliext::hash_set::rbegin
- cliext::hash_set::reference
- cliext::hash_set::rehash
- cliext::hash_set::rend
- cliext::hash_set::reverse_iterator
- cliext::hash_set::size
- cliext::hash_set::size_type
- cliext::hash_set::swap
- cliext::hash_set::to_array
- cliext::hash_set::upper_bound
- cliext::hash_set::value_comp
- cliext::hash_set::value_compare
- cliext::hash_set::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_set class [STL/CLR]
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
- hash_set member [STL/CLR]
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
ms.assetid: d110e356-ba3e-4e52-9e2d-d997bf975c96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c701bfa64e96594050ddaf46d56c12849a0ad30
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079752"
---
# <a name="hashset-stlclr"></a>hash_set (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `hash_set` do zarządzania sekwencję elementów jako tablicy skrótów, każdego wpisu tabeli przechowywania dwukierunkowy połączone listy węzłów i w każdym węźle przechowywania jeden element. Wartość każdego elementu jest używany jako klucz porządkowania sekwencji.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    ref class hash_set  
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
 Key  
 Typ części klucza elementu w kontrolowanej sekwencji.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>Deklaracje  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[hash_set::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[hash_set::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|  
|[hash_set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[hash_set::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[hash_set::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs umożliwiający kontenera.|  
|[hash_set::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_set::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[hash_set::hasher (STL/CLR)](#hasher)|Delegat funkcji skrótu dla klucza.|  
|[hash_set::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|  
|[hash_set::key_compare (STL/CLR)](#key_compare)|Delegat porządkowania dla dwa klucze.|  
|[hash_set::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|  
|[hash_set::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[hash_set::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[hash_set::size_type (STL/CLR)](#size_type)|Typ (nieujemną) odległość między dwoma elementami.|  
|[hash_set::value_compare (STL/CLR)](#value_compare)|Delegat porządkowania dla dwóch wartości elementu.|  
|[hash_set::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[hash_set::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|  
|[hash_set::bucket_count (STL/CLR)](#bucket_count)|Zlicza zasobników.|  
|[hash_set::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|  
|[hash_set::count (STL/CLR)](#count)|Liczba elementów pasujących określonego klucza.|  
|[hash_set::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[hash_set::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|  
|[hash_set::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[hash_set::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|  
|[hash_set::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[hash_set::hash_delegate (STL/CLR)](#hash_delegate)|Kopiuje delegat wyznaczania wartości skrótu z kluczem.|  
|[hash_set::hash_set (STL/CLR)](#hash_set)|Konstruuje obiekt kontenera.|  
|[hash_set::insert (STL/CLR)](#insert)|Dodaje elementy.|  
|[hash_set::key_comp (STL/CLR)](#key_comp)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[hash_set::load_factor (STL/CLR)](#load_factor)|Oblicza średnią liczbę elementów na przedział.|  
|[hash_set::lower_bound (STL/CLR)](#lower_bound)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[hash_set::make_value (STL/CLR)](#make_value)|Tworzy obiekt wartość.|  
|[hash_set::max_load_factor (STL/CLR)](#max_load_factor)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[hash_set::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[hash_set::rehash (STL/CLR)](#rehash)|Przebudowuje tabelę mieszania.|  
|[hash_set::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[hash_set::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[hash_set::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|  
|[hash_set::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[hash_set::upper_bound (STL/CLR)](#upper_bound)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[hash_set::value_comp (STL/CLR)](#value_comp)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[hash_set::operator= (STL/CLR)](#op)|Zastępuje kontrolowanej sekwencji.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|IHash\<klucza, wartość >|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu w sekwencji, które kontroluje jako poszczególne węzły połączonej listy dwukierunkowego. Aby przyśpieszyć dostępu, obiekt przechowuje zróżnicowanych długość tablicy wskaźników do listy (tablicy skrótów) efektywne zarządzanie całą listę sekwencję podlist, lub pakiety w ramach Agreement. Wstawia elementy na zasobnik, który utrzymuje uporządkowanych, zmieniając łącza między węzłami, nigdy nie, kopiując zawartość z jednego węzła do innego. Oznacza to, można wstawiać i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.  
  
 Obiekt porządkuje każdego zasobnika kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<=(key_type, key_type)`.  
  
 Dostęp do obiektu delegowanego przechowywanych przez wywołanie funkcji Członkowskich [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Obiekt delegowany musi definiować równoważne kolejności między kluczami typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)` Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y) && key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Reguły porządkowania zachowuje się jak `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` lub `operator==(key_type, key_type)` definiuje kolejność eqivalent.  
  
 Należy pamiętać, że kontener zagwarantuje tylko elementy którego klucze będą miały równoważne porządkowanie (i które skrót do tej samej wartości całkowitej) to sąsiadujących ze sobą w pojemniku. W odróżnieniu od klasy szablonu [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md), obiekt klasy szablonu `hash_set` zagwarantuje to unikatowy kluczy dla wszystkich elementów. (Nie dwa klucze jest równoważne kolejności).  
  
 Obiekt Określa, które zasobnika powinna zawierać klucz porządkowania przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` można uzyskać wartość całkowitą, która jest zależna od wartości klucza. Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to funkcja `System::Object::hash_value(key_type)`. Oznacza to, żadnych kluczy `X` i `Y`:  
  
 `hash_delegate()(X)` Zwraca takiego samego wyniku całkowitą przy każdym wywołaniu.  
  
 Jeśli `X` i `Y` mają równoważne określania kolejności, następnie `hash_delegate()(X)` powinien zwrócić takiego samego wyniku całkowitą jako `hash_delegate()(Y)`.  
  
 Każdy element służy jako klucz i wartość. Sekwencja jest reprezentowana w taki sposób, który umożliwia wyszukiwanie, wstawiania i usuwania elementu umownego z liczba operacji, która jest niezależna od liczby elementów w sekwencji (czas stałej)--co najmniej w najlepszym przypadku. Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Jeśli wartości skrótu nie są dystrybuowane jednolicie, jednak tablicy skrótów można dwa degeneracji. W extreme — dla funkcji skrótu, która zawsze zwraca tę samą wartość — wyszukiwanie, wstawiania i usuwania są proporcjonalny do liczby elementów w sekwencji (czas liniowej). Kontener usiłują wybierz funkcji skrótu uzasadnione, Zasobnik średniej wielkości, a rozmiar tablicy skrótów (całkowita liczba zasobników), ale możesz zastąpić dowolne z tych opcji. Zobacz na przykład funkcje [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) i [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_set — obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora hash_set, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu hash_set bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Hash_set iterator przechowuje dojścia do węzła hash_set skojarzony, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Hash_set iterator pozostaje ważny tak długo, jak jego węzła hash_set skojarzony jest skojarzony z niektórych hash_set. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="members"></a>Elementy członkowskie

## <a name="begin"></a> hash_set::BEGIN (STL/CLR)
Określa początek kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dwukierunkowego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub bezpośrednio po zakończeniu pustej sekwencji. Służy do uzyskania iterację wyznacza `current` początku kontrolowanej sekwencji, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_begin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_set::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  

## <a name="bucket_count"></a> hash_set::bucket_count (STL/CLR)
Zlicza zasobników.  
  
### <a name="syntax"></a>Składnia  
  
```  
int bucket_count();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie zwraca bieżącą liczbę zasobników. Można użyć do określenia rozmiaru tablicy skrótów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_bucket_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="clear"></a> hash_set::Clear (STL/CLR)
Usuwa wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje funkcję elementu członkowskiego [hash_set::erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md) `(` [hash_set::begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md) `(),` [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="const_iterator"></a> hash_set::const_iterator (STL/CLR)
Typ iteratora stałego dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T2` który może służyć jako iterator stałej dwukierunkowego, dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_set::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> hash_set::const_reference (STL/CLR)
Typ stałego odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano stałej odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_set::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_set::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> hash_set::const_reverse_iterator (STL/CLR)
Typ stałej iteratora wstecznego w kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T4` który może służyć jako stałej iteratora wstecznego w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_set::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="count"></a> hash_set::Count (STL/CLR)
Wyszukuje liczbę elementów pasujących do określonego klucza.  
  
### <a name="syntax"></a>Składnia  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę elementów w kontrolowanej sekwencji mające porządkowanie równoważne z `key`. Można użyć do określenia liczby elementów aktualnie w kontrolowanej sekwencji zgodne z określonym kluczem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="difference_type"></a> hash_set::difference_type (STL/CLR)
Typy podpisane odległość między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczba ujemna prawdopodobnie elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_set::difference_type diff = 0;   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_set::iterator it = c1.end(); it != c1.begin(); --it)   
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

## <a name="empty"></a> hash_set::EMPTY (STL/CLR)
Sprawdza, czy nie ma żadnych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wartość true dla pustego kontrolowanej sekwencji. Jest to równoważne [hash_set::size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md)`() == 0`. Można użyć do sprawdzenia, czy hash_set jest pusta.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_empty.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="end"></a> hash_set::end (STL/CLR)
Określa koniec kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dwukierunkowego tego punkty bezpośrednio po zakończeniu kontrolowanej sekwencji. Służy do uzyskania iterację Określa koniec kontrolowanej sekwencji; jego stan zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_end.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_set::iterator it = c1.end();   
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

## <a name="equal_range"></a> hash_set::equal_range (STL/CLR)
Wyszukuje zakres, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca parę Iteratory `cliext::pair<iterator, iterator>(` [hash_set::lower_bound (STL/CLR)](../dotnet/hash-set-lower-bound-stl-clr.md) `(key),` [hash_set::upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md)`(key))`. Można użyć do określenia zakresu elementów aktualnie w kontrolowanej sekwencji zgodne z określonym kluczem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
typedef Myhash_set::pair_iter_iter Pairii;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="erase"></a> hash_set::ERASE (STL/CLR)
Usuwa elementy z określonych pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu, aby wymazać.  
  
 klawisz  
 Wartość klucza, aby wymazać.  
  
 ostatni  
 Koniec zakresu, aby wymazać.  
  
 gdzie  
 Element, aby wymazać.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez `where`i zwraca iterację wyznacza pierwszy element pozostałych poza element usunięty, lub [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `()` Jeśli nie zawiera żadnego takiego elementu. Umożliwia ona Usuń pojedynczy element.  
  
 Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`) i zwraca iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub `end()` w przypadku braku takiego elementu istnieje.. Można użyć do usunięcia zero lub więcej elementów ciągłe.  
  
 Trzeci funkcji członkowskiej usuwa dowolny element kontrolowanej sekwencji, którego klucz został równoważne kolejności do `key`i zwraca liczbę liczba elementów usuniętych. Można użyć do usunięcia, a liczba wszystkie elementy zgodne z określonym kluczem.  
  
 Każdy element usunięcia czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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
    Myhash_set::iterator it = c1.end();   
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

## <a name="find"></a> hash_set::Find (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli co najmniej jednego elementu w kontrolowanej sekwencji ma porządkowanie równoważne z `key`, funkcją członkowską zwracającą iterator wyznaczenie jednego z tych elementów; w przeciwnym razie zwraca [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `()`. Umożliwia ona obecnie zlokalizować elementu w kontrolowanej sekwencji zgodny z określonym kluczem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_find.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="generic_container"></a> hash_set::generic_container (STL/CLR)
Typ ogólny interfejs umożliwiający kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IHash<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano ogólny interfejs dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_generic_container.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
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

## <a name="generic_iterator"></a> hash_set::generic_iterator (STL/CLR)
Typ iteratora do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano iteratora rodzajowy, używaną z ogólnym interfejsem dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_iterator gcit = gc1->begin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="generic_reverse_iterator"></a> hash_set::generic_reverse_iterator (STL/CLR)
Typ odwrotnej iteratora do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano ogólny iteratora odwrotnej służący z ogólnym interfejsem dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
```  
  
## <a name="generic_value"></a> hash_set::generic_value (STL/CLR)
Typ elementu do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano typu obiektu `GValue` opisujący wartość elementu przechowywane do użytku ogólnego interfejs dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_iterator gcit = gc1->begin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="hash_delegate"></a> hash_set::hash_delegate (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
### <a name="syntax"></a>Składnia  
  
```  
hasher^ hash_delegate();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca delegata służący do konwertowania wartości klucza na liczbę całkowitą. Służy do wyznaczania wartości skrótu klucza.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  

## <a name="hash_set"></a> hash_set::hash_set (STL/CLR)
Konstruuje obiekt kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 hashfn  
 Hash — funkcja kluczy mapowania do zasobników.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 pred  
 Porządkowanie predykatu w kontrolowanej sekwencji.  
  
 w prawo  
 Obiekt lub zakresu do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `hash_set();`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów przy użyciu domyślnego porządkowanie predykatu `key_compare()`i przy użyciu funkcji skrótu domyślne. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `explicit hash_set(key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, określony predykat porządkowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, przy użyciu określonego sortowania funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_set(hash_set<Key>% right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right.begin()`, `right.end()`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt hash_set `right`, przy użyciu domyślnego sortowania predykat i funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_set(hash_set<Key>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right->begin()`, `right->end()`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt hash_set `right`, przy użyciu domyślnego sortowania predykat i funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji określony predykat porządkowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji o określonej porządkowania funkcji wyznaczania wartości skrótu i predykatu.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający, przy użyciu określonego sortowania predykat i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający o określonej porządkowania funkcji wyznaczania wartości skrótu i predykatu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
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

## <a name="hasher"></a> hash_set::hasher (STL/CLR)
Delegat funkcji skrótu dla klucza.  
  
### <a name="syntax"></a>Składnia  
  
```  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano delegata, który konwertuje wartości klucza na liczbę całkowitą.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  

## <a name="insert"></a> hash_set::INSERT (STL/CLR)
Dodaje elementy.  
  
### <a name="syntax"></a>Składnia  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 w prawo  
 Wyliczenie do wstawienia.  
  
 Val  
 Wartość klucza do wstawienia.  
  
 gdzie  
 Gdzie w kontenerze, aby wstawić (tylko wskazówka).  
  
### <a name="remarks"></a>Uwagi  
 Każda z funkcji Członkowskich wstawia sekwencję określony przez pozostałych argumentów operacji.  
  
 Pierwszy funkcji członkowskiej usiłują Wstaw element z wartością `val`i zwraca pary wartości `X`. Jeśli `X.second` ma wartość true, `X.first` wyznacza nowo wstawionej elementu; w przeciwnym razie `X.first` wskazuje element z równoważne porządkowania, która już istnieje i jest wstawiany nie nowego elementu. Umożliwia ona wstawić jeden element.  
  
 Drugi funkcji członkowskiej wstawia element z wartością `val`za pomocą `where` jako wskazówkę (Aby poprawić wydajność) i zwraca iterację wyznacza nowo wstawiony element. Umożliwia ona pojedynczy element, który może być obok elementu, który znasz Wstaw.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Każdy element wstawiania czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji. Wstawiania może występować w amortyzowanego stałej czasu jednak podane wskazówki, który wskazuje element sąsiadujące punkt wstawiania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
typedef Myhash_set::pair_iter_bool Pairib;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
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
    Myhash_set c2;   
    Myhash_set::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_set c3;   
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
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  

## <a name="iterator"></a> hash_set::iterator (STL/CLR)
Typ iteratora dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T1` który może służyć jako iterator dwukierunkowego, dla kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_set::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> hash_set::key_comp (STL/CLR)
Kopiuje porządkowania delegowanie dla dwa klucze.  
  
### <a name="syntax"></a>Składnia  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca delegata porządkowania porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwa klucze.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
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

## <a name="key_comp"></a> hash_set::key_comp (STL/CLR)
Kopiuje porządkowania delegowanie dla dwa klucze.  
  
### <a name="syntax"></a>Składnia  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca delegata porządkowania porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwa klucze.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
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

## <a name="key_compare"></a> hash_set::key_compare (STL/CLR)
Delegat porządkowania dla dwa klucze.  
  
### <a name="syntax"></a>Składnia  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem delegata, który określa kolejność argumentów klucza.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
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

## <a name="key_type"></a> hash_set::key_type (STL/CLR)
Typ klucza sortowania.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Key`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_set::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="load_factor"></a> hash_set::load_factor (STL/CLR)
Oblicza średnią liczbę elementów na przedział.  
  
### <a name="syntax"></a>Składnia  
  
```  
float load_factor();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `(float)` [hash_set::size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md) `() /` [hash_set::bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)`()`. Można użyć do określenia rozmiaru średni zasobnika.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="lower_bound"></a> hash_set::lower_bound (STL/CLR)
Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska Określa pierwszy element `X` w kontrolowanej sekwencji, który tworzy skrót do tego samego zasobnika jako `key` i ma równoważne kolejności do `key`. Jeśli żaden taki element istnieje, zwraca [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterację wyznacza `X`. Możesz użyć do zlokalizowania na początku sekwencji elementów aktualnie w kontrolowanej sekwencji, który jest zgodny z określonym kluczem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="make_value"></a> hash_set::make_value (STL/CLR)
Tworzy obiekt wartość.  
  
### <a name="syntax"></a>Składnia  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do użycia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `value_type` obiektu, którego klucz jest `key`. Można go użyć do zredagowania odpowiednie do użycia z wielu innych funkcji elementów członkowskich obiektu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(Myhash_set::make_value(L'a'));   
    c1.insert(Myhash_set::make_value(L'b'));   
    c1.insert(Myhash_set::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="max_load_factor"></a> hash_set::max_load_factor (STL/CLR)
Pobiera lub ustawia maksymalną liczbę elementów na przedział.  
  
### <a name="syntax"></a>Składnia  
  
```  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_factor  
 Maksymalna nowe obciążenia współczynnik do przechowywania.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element członkowski funkcja bieżący współczynnik przechowywanych maksymalne obciążenie. Można użyć do określenia rozmiar maksymalny średni zasobnika.  
  
 Drugi funkcji członkowskiej zastępuje współczynnik maksymalne obciążenie magazynu z `new_factor`. Nie automatycznego rehashing występuje do kolejnych insert.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="op"></a> hash_set::operator = (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
hash_set<Key>% operator=(hash_set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień kontrolowanej sekwencji kopię w kontrolowanej sekwencji `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_set c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> hash_set::rbegin (STL/CLR)
Określa początek odwróconej kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora, który wyznacza ostatniego elementu w kontrolowanej sekwencji lub poza początku pustej sekwencji. W związku z tym wyznacza `beginning` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` początku kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_set::reverse_iterator rit = c1.rbegin();   
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

## <a name="reference"></a> hash_set::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_set::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_set::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="rehash"></a> hash_set::rehash (STL/CLR)
Przebudowuje tabelę mieszania.  
  
### <a name="syntax"></a>Składnia  
  
```  
void rehash();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska odtwarza tablicy skrótów, upewniając się, że [hash_set::load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md) `() <=` [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md). W przeciwnym razie tablicy skrótów zwiększa rozmiar tylko w razie potrzeby po wstawieniu. (Nigdy nie automatycznie zmniejsza rozmiar.) Umożliwia ona dostosować rozmiar tablicy skrótów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="rend"></a> hash_set::rend (STL/CLR)
Określa koniec odwróconej kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora tego punktów poza początku kontrolowanej sekwencji. W związku z tym wyznacza `end` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_rend.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_set::reverse_iterator rit = c1.rend();   
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

## <a name="reverse_iterator"></a> hash_set::reverse_iterator (STL/CLR)
Typ odwrotnej iteratora w kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T3` który może służyć jako odwrotnej iteratora w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_set::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="size"></a> hash_set::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość kontrolowanej sekwencji. Można użyć do określenia liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli wszystkie najważniejsze informacje dotyczące tego, czy sekwencja ma rozmiar różną od zera, zobacz [hash_set::empty (STL/CLR)](../dotnet/hash-set-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="size_type"></a> hash_set::size_type (STL/CLR)
Typ podpisem odległość między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczbą nieujemną elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_set::size_type diff = 0;   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> hash_set::swap (STL/CLR)
Zamienia zawartości dwóch kontenerów.  
  
### <a name="syntax"></a>Składnia  
  
```  
void swap(hash_set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do wymiany zawartości z.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia kontrolowanej sekwencji między `this` i `right`. Robi to w czasie stałej i zgłasza żadnych wyjątków. Możesz używać go jako szybko do wymiany zawartości dwóch kontenerów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_set c2;   
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

## <a name="to_array"></a> hash_set::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona uzyskać kopię kontrolowanej sekwencji w postaci tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="upper_bound"></a> hash_set::upper_bound (STL/CLR)
Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska Określa ostatni element `X` w kontrolowanej sekwencji, który tworzy skrót do tego samego zasobnika jako `key` i ma równoważne kolejności do `key`. Jeśli nie zawiera żadnego takiego elementu lub `X` jest ostatniego elementu w kontrolowanej sekwencji zwraca [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`; w przeciwnym razie zwraca określający pierwszy element poza iteratora`X`. Umożliwia ona obecnie Znajdź koniec sekwencję elementów w kontrolowanej sekwencji, który jest zgodny z określonym kluczem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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

## <a name="value_comp"></a> hash_set::value_comp (STL/CLR)
Kopiuje porządkowania delegowanie dla dwóch wartości elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca delegata porządkowania porządkowania kontrolowanej sekwencji. Można użyć do porównania dwóch wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::value_compare^ kcomp = c1.value_comp();   
  
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

## <a name="value_compare"></a> hash_set::value_compare (STL/CLR)
Delegat porządkowania dla dwóch wartości elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem delegata, który określa kolejność argumentów wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::value_compare^ kcomp = c1.value_comp();   
  
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

## <a name="value_type"></a> hash_set::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `generic_value`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_hash_set_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_set::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  