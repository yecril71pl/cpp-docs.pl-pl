---
title: priority_queue — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cb2ee3fa52612ee3c6abae7a57046564c10c8afb
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376040"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
Klasa szablonu opisuje obiekt, który kontroluje różnej długości uporządkowane sekwencję elementów, które ma ograniczony dostęp. Użyj karty kontenera `priority_queue` do zarządzania kontenerem podstawowej jako kolejki priorytetowej.  
  
 W poniższym opisie `GValue` jest taka sama jak *wartość* o ile nie jest typem odwołania, w którym to przypadku jest `Value^`. Podobnie `GContainer` jest taka sama jak *kontenera* o ile nie jest typem odwołania, w którym to przypadku jest `Container^`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Wartość*  
 Typ elementu w kontrolowanej sekwencji.  
  
 *Kontener*  
 Typ podstawowy kontener.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext — / kolejki >  
  
 **Namespace:** cliext —  

## <a name="declarations"></a>Deklaracje  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|  
|[priority_queue::container_type (STL/CLR)](#container_type)|Typ podstawowy kontener.|  
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla karty kontenera.|  
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólnego interfejsu dla karty kontenera.|  
|[priority_queue::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[priority_queue::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Delegat szeregowania dla dwóch elementów.|  
|[priority_queue::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|  
|[priority_queue::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[priority_queue::get_container (STL/CLR)](#get_container)|Uzyskuje dostęp do podstawowych kontenera.|  
|[priority_queue::pop (STL/CLR)](#pop)|Usuwa element o priorytecie najwyższa.|  
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Konstruuje obiekt kontenera.|  
|[priority_queue::push (STL/CLR)](#push)|Dodaje nowy element.|  
|[priority_queue::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[priority_queue::top (STL/CLR)](#top)|Uzyskuje dostęp do elementów o najwyższym priorytecie.|  
|[priority_queue::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Kopiuje szeregowania delegata dla dwóch elementów.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](#top_item)|Uzyskuje dostęp do elementów o najwyższym priorytecie.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplikowanie obiektów.|  
|IPriorityQueue\<wartość, kontener >|Obsługa karty Ogólne kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia pamięć dla sekwencji za pośrednictwem podstawowych kontenera, typu `Container`, który przechowuje `Value` elementy i rośnie na żądanie. Zapewnia sekwencji uporządkowane jako stertę, najwyższy priorytet elementu (element najwyższego) łatwo dostępne i wymiennych. Obiekt ogranicza dostęp do wypychania nowych elementów i wyświetlanie tylko najwyższy priorytet elementu, implementowanie kolejki priorytetowej.  
  
 Obiekt porządkuje sekwencję którą kontroluje, przez wywołanie obiektu przechowywanej delegat typu [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania priority_queue —; Jeśli obiekt delegowany nie zostanie określony, wartością domyślną jest porównanie `operator<(value_type, value_type)`. Ten przechowywany obiekt jest dostępu przez wywołanie funkcji elementu członkowskiego [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Obiektu delegowanego musi powodować ścisłe słabe porządkowanie w wartościach typu [priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Oznacza to, dla dowolnego dwa klucze `X` i `Y`:  
  
 `value_comp()(X, Y)` Zwraca wynik tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `value_comp()(X, Y)` ma wartość true, następnie `value_comp()(Y, X)` musi mieć wartość false.  
  
 Jeśli `value_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany jest umieszczane przed `Y`.  
  
 Jeśli `!value_comp()(X, Y) && !value_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważną kolejność.  
  
 Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.)  
  
 Element najwyższy priorytet stanowi jeden z elementów, które nie są uporządkowane przed innym elementem.  
  
 Ponieważ podstawowy kontener przechowuje elementy uporządkowane jako sterty:  
  
 Kontener musi obsługiwać iteratorami dostępu swobodnego.  
  
 Elementy z równoważną kolejność może zostać zdjęte ze stosu w innej kolejności, nie zostały one przekazane. (Kolejność nie jest stabilna).  
  
 W związku z tym, zawierają kandydatami do bazowego kontenera [deque (STL/CLR)](../dotnet/deque-stl-clr.md) i [wektor (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="members"></a>Elementy członkowskie
  
## <a name="assign"></a> priority_queue::ASSIGN (STL/CLR)
Zamienia wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void assign(priority_queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Adapter kontenera do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego przypisuje `right.get_container()` do bazowego kontenera. Możesz użyć do zmiany całej zawartości kolejki.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mypriority_queue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
c a b  
```  

## <a name="const_reference"></a> priority_queue::const_reference (STL/CLR)
Typ stałego odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje stałe odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_const_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " c b a"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Mypriority_queue::const_reference cref = c1.top();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="container_type"></a> priority_queue::container_type (STL/CLR)
Typ podstawowy kontener.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Container value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla parametru szablonu `Container`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mypriority_queue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="difference_type"></a> priority_queue::difference_type (STL/CLR)
Typy odległości ze znakiem między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczba element prawdopodobnie ujemna.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_difference_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Mypriority_queue::difference_type diff = c1.size();   
    c1.push(L'd');   
    c1.push(L'e');   
    diff -= c1.size();   
    System::Console::WriteLine("pushing 2 = {0}", diff);   
  
// compute positive difference   
    diff = c1.size();   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("popping 3 = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 c a b  
pushing 2 = -2  
popping 3 = 3  
```  

## <a name="empty"></a> priority_queue::EMPTY (STL/CLR)
Sprawdza, czy nie ma żadnych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy priority_queue — jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_empty.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
```  
  
```Output  
 c a b  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="generic_container"></a> priority_queue::generic_container (STL/CLR)
Typ ogólny interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje ogólny interfejs dla tej klasy szablonu kontenera karty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
c a b  
d c b a  
e d b a c  
```  

## <a name="generic_value"></a> priority_queue::generic_value (STL/CLR)
Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje. (`GValue` jest `value_type` lub `value_type^` Jeśli `value_type` jest typem odwołania.)  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in priority order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Mypriority_queue::generic_value elem = gc1->top();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
c a b  
c b a  
```  

## <a name="get_container"></a> priority_queue::get_container (STL/CLR)
Uzyskuje dostęp do podstawowych kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
container_type get_container();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca bazowego kontenera. Umożliwia ona obejścia ograniczeń nałożonych przez otokę kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="op_as"></a> priority_queue::operator = (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Adapter kontenera do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mypriority_queue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
c a b  
c a b  
```  

## <a name="pop"></a> priority_queue::POP (STL/CLR)
Usuwa element proirity najwyższy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void pop();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa element najwyższy priorytet w kontrolowanej sekwencji musi być niepusta. Umożliwia ona skrócić czas kolejki przez jeden element w tle.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
b a  
```  

## <a name="priority_queue"></a> priority_queue::priority_queue (STL/CLR)
Konstruuje obiekt kontenera karty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>Parametry  
 *CD*  
 Kontener do skopiowania.  
  
 *pierwszy*  
 Początek zakresu do wstawienia.  
  
 *ostatni*  
 Koniec zakresu do wstawienia.  
  
 *P.*  
 Kolejność predykat dla kontrolowanej sekwencji.  
  
 *right*  
 Obiekt lub zakresu do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `priority_queue();`  
  
 tworzy pustego kontenera zawinięty, przy użyciu domyślnego porządkowanie predykat. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, przy użyciu domyślnego porządkowanie predykat.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Tworzy opakowana kontener, który jest kopią `right.get_container()`, z predykatem szeregowania `right.value_comp()`. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt kolejki *prawo*, za pomocą tego samego sortowania predykat.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Tworzy opakowana kontener, który jest kopią `right->get_container()`, z predykatem szeregowania `right->value_comp()`. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt kolejki `*right`, za pomocą tego samego sortowania predykat.  
  
 Konstruktor:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 tworzy pustego kontenera opakowana z predykatem szeregowania *pred*. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, z określonym predykatem szeregowania.  
  
 Konstruktor:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 tworzy pustego kontenera opakowana z predykatem szeregowania *pred*, następnie wypycha wszystkie elementy *CD* używasz do określenia początkowej kontrolowanej sekwencji z istniejącego kontenera za pomocą określony predykat szeregowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 tworzy pustego kontenera opakowana z predykatem sortowania domyślnego, a następnie wypycha sekwencji [`first`, `last`). Umożliwia ona określenie początkowej kontrolowanej sekwencji z określonym eqeuence, z określonym predykatem szeregowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 tworzy pustego kontenera opakowana z predykatem szeregowania *pred*, następnie wypycha sekwencji [`first`, `last`). Umożliwia ona określenie początkowej kontrolowanej sekwencji z określonym seqeuence, z określonym predykatem szeregowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 tworzy pustego kontenera opakowana z predykatem szeregowania *pred*, następnie wypycha wszystkie elementy *CD* plus sekwencji [`first`, `last`). Umożliwia ona określenie początkowej kontrolowanej sekwencji z istniejącego kontenera i określonego seqeuence, z określonym predykatem szeregowania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="push"></a> priority_queue::push (STL/CLR)
Dodaje nowy element.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void push(value_type val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego wstawia element z wartością `val` w kontrolowanej sekwencji i zmienia kolejność kontrolowanej sekwencji, aby zachować dyscypliny sterty. Umożliwia ona Dodawanie innego elementu do kolejki.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  
  
## <a name="reference"></a> priority_queue::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
x a b  
```  

## <a name="size"></a> priority_queue::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// pop an item and reinspect   
    c1.pop();   
    System::Console::WriteLine("size() = {0} after popping", c1.size());   
  
// add two elements and reinspect   
    c1.push(L'a');   
    c1.push(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 c a b  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  

## <a name="size_type"></a> priority_queue::size_type (STL/CLR)
Typ odległości ze znakiem między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczby nieujemnej wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_priority_queue_size_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mypriority_queue::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 c a b  
size difference = 2  
```  
  
## <a name="to_array"></a> priority_queue::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_to_array.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push(L'd');   
    for each (wchar_t elem in c1.get_container())   
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
d c b a  
c a b  
```  

## <a name="top"></a> priority_queue::Top (STL/CLR)
Uzyskuje dostęp do elementów o najwyższym priorytecie.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
reference top();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca odwołanie do elementu górnej (najwyższy priorytet) kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona dostęp do elementu najwyższy priorytet w przypadku, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_top.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  

## <a name="top_item"></a> priority_queue::top_item (STL/CLR)
Uzyskuje dostęp do elementów o najwyższym priorytecie.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Uwagi  
 Właściwość uzyskuje dostęp do góry (najwyższy priorytet) elementu kontrolowanej sekwencji musi być niepusta. Możesz użyć do odczytu lub zapisu elementu najwyższy priorytet, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_top_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 c a b  
top_item = c  
 x a b  
```  

## <a name="value_comp"></a> priority_queue::value_comp (STL/CLR)
Kopiuje szeregowania delegata dla dwóch elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwie wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_value_comp.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="value_compare"></a> priority_queue::value_compare (STL/CLR)
Delegat szeregowania dla dwóch wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
binary_delegate<value_type, value_type, int> value_compare;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla delegata, która określa, czy pierwszy argument był zamówiony przed drugim.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_value_compare.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="value_type"></a> priority_queue::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla parametru szablonu *wartość*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  