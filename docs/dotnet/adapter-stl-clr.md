---
title: Karta (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a472284df67993a65de98df7db698ea533451ea3
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079439"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
Nagłówek STL/CLR `<cliext/adapter>` określa dwóch szablonów klas (`collection_adapter` i `range_adapter`), a funkcja szablonu `make_collection`.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <cliext/adapter>  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/karty >  
  
 **Namespace:** cliext 
  
## <a name="declarations"></a>Deklaracje  
  
|Class|Opis|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](#collection_adapter)|Opakowuje kolekcji biblioteki klasy podstawowej (BCL) jako zakres.|  
|[range_adapter (STL/CLR)](#range_adapter)|Opakowuje zakres jako kolekcja BCL.|  

|Funkcja|Opis|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](#make_collection)|Tworzy kartą zakresu przy użyciu pary iteratora.|   
  
## <a name="members"></a>Elementy członkowskie

## <a name="collection_adapter"></a> collection_adapter — (STL/CLR)
Opakowuje kolekcji .NET do użycia jako kontenera STL/CLR. A `collection_adapter` to klasa szablonu, który opisuje prostego obiektu kontenera STL/CLR. Opakowuje interfejsu biblioteki klasy podstawowej (BCL) i zwraca pary iteratora używanej do manipulowania kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
##### <a name="parameters"></a>Parametry  
 Coll  
 Typ kolekcji opakowana.  
  
### <a name="specializations"></a>Specjalizacje  
  
|Specjalizacji|Opis|  
|--------------------|-----------------|  
|Interfejs IEnumerable|Sekwencje przez elementy.|  
|Interfejs ICollection|Przechowuje grupę elementów.|  
|IList|Obsługuje uporządkowane grupy elementów.|  
|Element IDictionary|Obsługa zestaw {klucza, wartość} pary.|  
|Interfejs IEnumerable\<wartość >|Sekwencje za pośrednictwem typu elementów.|  
|Interfejs ICollection\<wartość >|Przechowuje grupę elementów typu.|  
|IList\<wartość >|Obsługuje uporządkowane grupy elementów typu.|  
|IDictionary\<wartość >|Funkcja obsługuje zestaw typu {klucza, wartość} pary.|  
  
### <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[collection_adapter::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|  
|[collection_adapter::key_type (STL/CLR)](#key_type)|Typ klucza słownika.|  
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|Typ wartości słownika.|  
|[collection_adapter::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[collection_adapter::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[collection_adapter::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](#base)|Określa interfejs BCL opakowana.|  
|[collection_adapter::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|  
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Tworzy obiekt karty.|  
|[collection_adapter::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|  
|[collection_adapter::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[collection_adapter::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Zastępuje przechowywanych dojście BCL.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa szablon służy do manipulowania kontener BCL jako kontenera STL/CLR. `collection_adapter` Przechowuje dojście do interfejsu BCL, który z kolei kontroluje sekwencję elementów. A `collection_adapter` obiektu `X` zwraca parę wejściowych Iteratory `X.begin()` i `X.end()` umożliwia odwiedź elementów, w kolejności. Niektóre specjalizacji pozwalają również zapisu `X.size()` do określania długości kontrolowanej sekwencji.  

## <a name="base"></a> collection_adapter::Base (STL/CLR)
Określa interfejs BCL opakowana.  
  
### <a name="syntax"></a>Składnia  
  
```  
Coll^ base();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca przechowywanych dojście interfejsu BCL.  
  
### <a name="example"></a>Przykład  
  
```cpp
// cliext_collection_adapter_base.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  

## <a name="begin"></a> collection_adapter::BEGIN (STL/CLR)
Określa początek kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca określający pierwszego elementu w kontrolowanej sekwencji lub bezpośrednio po zakończeniu pustej sekwencji wejściowych iteratora.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_begin.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
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

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)
Tworzy obiekt karty.  
  
### <a name="syntax"></a>Składnia  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Parametry  
 — kolekcja  
 BCL dojście do zakodowania.  
  
 w prawo  
 Obiekt przeznaczony do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `collection_adapter();`  
  
 Inicjuje przechowywanych dojścia o `nullptr`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Inicjuje przechowywanych dojścia o `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Inicjuje przechowywanych dojścia o `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(Coll^ collection);`  
  
 Inicjuje przechowywanych dojścia z o `collection`.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)
Typy podpisane odległość między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczba podpisanego elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_collection_adapter_difference_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mycoll::difference_type diff = 0;   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="end"></a> collection_adapter::end (STL/CLR)
Określa koniec kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wejściowych iteratora tego punkty bezpośrednio po zakończeniu kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_collection_adapter_end.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)
Typ iteratora dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T1` który może służyć jako iteratora wejściowego w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_iterator.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_type"></a> collection_adapter::key_type (STL/CLR)
Typ klucza słownika.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Key`, w specjalizacji dla `IDictionary` lub `IDictionary<Value>`; w przeciwnym razie nie jest zdefiniowany.  
  
### <a name="example"></a>Przykład  
  
```cpp
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)
Typ wartości słownika.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Value mapped_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Value`, w specjalizacji dla `IDictionary` lub `IDictionary<Value>`; w przeciwnym razie nie jest zdefiniowany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_mapped_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)
Zastępuje przechowywanych dojście BCL.  
  
### <a name="syntax"></a>Składnia  
  
```  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Karta do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień przechowywanych dojście BCL kopię uchwytu BCL przechowywanych w `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_collection_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mycoll c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="reference"></a> collection_adapter::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_collection_adapter_reference.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mycoll::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="size"></a> collection_adapter::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość kontrolowanej sekwencji. Nie jest zdefiniowany w specjalizacji dla `IEnumerable` lub `IEnumerable<Value>`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_size.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)
Typ podpisem odległość między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczbą nieujemną elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_size_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    Mycoll::size_type size = c1.size();   
    System::Console::WriteLine("size() = {0}", size);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="swap"></a> collection_adapter::swap (STL/CLR)
Zamienia zawartości dwóch kontenerów.  
  
### <a name="syntax"></a>Składnia  
  
```  
void swap(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do wymiany zawartości z.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia przechowywanych uchwytów BCL między `*this` i `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp
// cliext_collection_adapter_swap.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
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
x x x x x  
x x x x x  
a b c  
```  

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Value`, jeśli jest obecny w specjalizacji; w przeciwnym razie jest synonimem `System::Object^`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_collection_adapter_value_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display contents " a b c" using value_type   
    for (Mycoll::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mycoll::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="make_collection"></a> make_collection — (STL/CLR)
Wprowadź `range_adapter` z pary iteratora.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Iter`  
 Typ Iteratory opakowana.  
  
 `first`  
 Pierwszy iteratora do zakodowania.  
  
 `last`  
 Drugi iteratora do zakodowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `gcnew range_adapter<Iter>(first, last)`. Można go użyć do utworzenia `range_adapter<Iter>` obiektu z pary Iteratory.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_make_collection.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in d1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Collections::ICollection^ p1 =   
        cliext::make_collection(d1.begin(), d1.end());   
    System::Console::WriteLine("Count = {0}", p1->Count);   
    System::Console::WriteLine("IsSynchronized = {0}",   
        p1->IsSynchronized);   
    System::Console::WriteLine("SyncRoot not nullptr = {0}",   
        p1->SyncRoot != nullptr);   
  
// copy the sequence   
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);   
  
    a1[0] = L'|';   
    p1->CopyTo(a1, 1);   
    a1[4] = L'|';   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
Count = 3  
IsSynchronized = False  
SyncRoot not nullptr = True  
 | a b c |  
```  

## <a name="range_adapter"></a> range_adapter — (STL/CLR)
Klasa szablonu, która opakowuje parę Iteratory, które są używane do implementowania kilka interfejsów biblioteki klasy podstawowej (BCL). Range_adapter — służy do manipulowania zakres STL/CLR, tak jakby był on kolekcji BCL.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 ITER  
 Typ skojarzony z Iteratory opakowana.  
  
### <a name="members"></a>Elementy członkowskie  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Tworzy obiekt karty.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Zastępuje pary iteratora przechowywane.|  
  
### <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Wykonuje iterację elementów w kolekcji.|  
|<xref:System.Collections.ICollection>|Przechowuje grupę elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Wykonuje iterację typu elementów w kolekcji.|  
|<xref:System.Collections.Generic.ICollection%601>|Przechowuje grupę elementów typu.|  
  
### <a name="remarks"></a>Uwagi  
 Range_adapter — przechowuje parę Iteratory, która z kolei określa sekwencję elementów. Obiekt implementuje cztery interfejsów BCL, które pozwalają iterowania po elementach, w kolejności. Ta klasa szablon służy do modyfikowania zakresów STL/CLR, podobnie jak kontenery BCL.  

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)
Zastępuje pary iteratora przechowywane.  
  
### <a name="syntax"></a>Składnia  
  
```  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Karta do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień pary iteratora przechowywanych kopię pary iteratora przechowywanych w `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_range_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Myrange c1(d1.begin(), d1.end());   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)
Tworzy obiekt karty.  
  
### <a name="syntax"></a>Składnia  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Pierwszy iteratora do zakodowania.  
  
 ostatni  
 Drugi iteratora do zakodowania.  
  
 w prawo  
 Obiekt przeznaczony do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `range_adapter();`  
  
 Inicjuje pary iteratora przechowywanych z Iteratory domyślne skonstruowany.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 Inicjuje pary iteratora przechowywanych przez skopiowanie pary przechowywane w `right`.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 Inicjuje pary iteratora przechowywanych przez skopiowanie pary przechowywane w `*right`.  
  
 Konstruktor:  
  
 `range_adapter(Iter^ first, last);`  
  
 Inicjuje pary iteratora przechowywane z `first` i `last`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  