---
title: kolejki (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::queue::assign
- cliext::queue::back
- cliext::queue::back_item
- cliext::queue::const_reference
- cliext::queue::container_type
- cliext::queue::difference_type
- cliext::queue::empty
- cliext::queue::front
- cliext::queue::front_item
- cliext::queue::generic_container
- cliext::queue::generic_value
- cliext::queue::get_container
- cliext::queue::operator=
- cliext::queue::pop
- cliext::queue::push
- cliext::queue::queue
- cliext::queue::reference
- cliext::queue::size
- cliext::queue::size_type
- cliext::queue::to_array
- cliext::queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- queue member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: adf65c4af70b0ba6bc1f089576d69160ab21a5b6
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376000"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającym pierwszy na wejściu dostęp. Użyj karty kontenera `queue` do zarządzania kontenerem podstawowej jako kolejki.  
  
 W poniższym opisie `GValue` jest taka sama jak *wartość* o ile nie jest typem odwołania, w którym to przypadku jest `Value^`. Podobnie `GContainer` jest taka sama jak *kontenera* o ile nie jest typem odwołania, w którym to przypadku jest `Container^`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|  
|[queue::container_type (STL/CLR)](#container_type)|Typ podstawowy kontener.|  
|[queue::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[queue::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla karty kontenera.|  
|[queue::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólnego interfejsu dla karty kontenera.|  
|[queue::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[queue::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[queue::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|  
|[queue::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|  
|[queue::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[queue::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|  
|[queue::get_container (STL/CLR)](#get_container)|Uzyskuje dostęp do podstawowych kontenera.|  
|[queue::pop (STL/CLR)](#pop)|Usuwa pierwszy element.|  
|[queue::push (STL/CLR)](#push)|Dodaje nowy element ostatni.|  
|[queue::queue (STL/CLR)](#queue)|Konstruuje obiekt kontenera.|  
|[queue::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[queue::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|  
|[queue::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (queue) (STL/CLR)](#op_neq)|Określa, czy `queue` obiekt nie jest równy innemu `queue` obiektu.|  
|[operator< (queue) (STL/CLR)](#op_lt)|Określa, czy `queue` obiekt jest mniejszy niż inny `queue` obiektu.|  
|[operator<= (queue) (STL/CLR)](#op_lteq)|Określa, czy `queue` obiekt jest mniejszy niż lub równy innemu `queue` obiektu.|  
|[operator== (queue) (STL/CLR)](#op_eq)|Określa, czy `queue` obiekt jest równy innemu `queue` obiektu.|  
|[operator> (queue) (STL/CLR)](#op_gt)|Określa, czy `queue` obiekt jest większy niż inny `queue` obiektu.|  
|[operator>= (queue) (STL/CLR)](#op_gteq)|Określa, czy `queue` obiekt jest większy niż lub równy innemu `queue` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplikowanie obiektów.|  
|IQueue\<wartość, kontener >|Obsługa karty Ogólne kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia pamięć dla sekwencji za pośrednictwem podstawowych kontenera, typu `Container`, który przechowuje `Value` elementy i rośnie na żądanie. Obiekt ogranicza dostęp do właśnie wypychanie pierwszego elementu, a usuwanie ostatniego elementu, implementowanie pierwszy na wejściu kolejki (znany także jako kolejki FIFO lub po prostu kolejki).  
  
## <a name="members"></a>Elementy członkowskie

## <a name="assign"></a> Queue::ASSIGN (STL/CLR)
Zamienia wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void assign(queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Adapter kontenera do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego przypisuje `right.get_container()` do bazowego kontenera. Możesz użyć do zmiany całej zawartości kolejki.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Myqueue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="back"></a> Queue::back (STL/CLR)
Uzyskuje dostęp do ostatniego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
reference back();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca odwołanie do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona dostęp do ostatniego elementu, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_back.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> Queue::back_item (STL/CLR)
Uzyskuje dostęp do ostatniego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Uwagi  
 Właściwość uzyskuje dostęp do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu ostatniego elementu, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_back_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="const_reference"></a> Queue::const_reference (STL/CLR)
Typ stałego odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje stałe odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_const_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Myqueue::const_reference cref = c1.front();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="container_type"></a> Queue::container_type (STL/CLR)
Typ podstawowy kontener.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Container value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla parametru szablonu `Container`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Myqueue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="difference_type"></a> Queue::difference_type (STL/CLR)
Typy odległości ze znakiem między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczba element prawdopodobnie ujemna.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_difference_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Myqueue::difference_type diff = c1.size();   
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
 a b c  
pushing 2 = -2  
popping 3 = 3  
```  

## <a name="empty"></a> Queue::EMPTY (STL/CLR)
Sprawdza, czy nie ma żadnych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy kolejka jest pusta.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_empty.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="front"></a> Queue::Front (STL/CLR)
Uzyskuje dostęp do pierwszego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
reference front();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca odwołanie do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona dostęp do pierwszego elementu, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_front.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

## <a name="front_item"></a> Queue::front_item (STL/CLR)
Uzyskuje dostęp do pierwszego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property value_type front_item;  
```  
  
### <a name="remarks"></a>Uwagi  
 Właściwość uzyskuje dostęp do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu pierwszego elementu, gdy wiadomo, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_front_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter last item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

## <a name="generic_container"></a> Queue::generic_container (STL/CLR)
Typ ogólny interfejs dla karty kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Microsoft::VisualC::StlClr::IQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje ogólny interfejs dla tej klasy szablonu kontenera karty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myqueue::generic_container^ gc1 = %c1;   
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
a b c  
a b c  
a b c d  
a b c d e  
```  

## <a name="generic_value"></a> Queue::generic_value (STL/CLR)
Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje. (`GValue` jest `value_type` lub `value_type^` Jeśli `value_type` jest typem odwołania.)  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a b c  
```  

## <a name="get_container"></a> Queue::get_container (STL/CLR)
Uzyskuje dostęp do podstawowych kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
container_type^ get_container();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca bazowego kontenera. Umożliwia ona obejścia ograniczeń nałożonych przez otokę kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
```  

## <a name="op_as"></a> Queue::operator = (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
queue <Value, Container>% operator=(queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Adapter kontenera do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
a b c  
```  

## <a name="pop"></a> Queue::POP (STL/CLR)
Usuwa ostatni element.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void pop();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona skrócić czas kolejki przez jeden element w tle.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
b c  
```  

## <a name="push"></a> Queue::push (STL/CLR)
Dodaje nowy element ostatni.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void push(value_type val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego dodaje element z wartością `val` na końcu kolejki. Umożliwia ona dołączyć element w kolejce.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
```  

## <a name="queue"></a> Queue::Queue (STL/CLR)
Konstruuje obiekt kontenera karty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>Parametry  
 *right*  
 Obiekt do skopiowania.  
  
 *opakowana*  
 Opakowana kontener do użycia.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `queue();`  
  
 tworzy pusty kontener opakowana. Umożliwia ona określenie pustą kontrolowaną sekwencję początkowej.  
  
 Konstruktor:  
  
 `queue(queue<Value, Container>% right);`  
  
 Tworzy opakowana kontener, który jest kopią `right.get_container()`. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt kolejki *prawo*.  
  
 Konstruktor:  
  
 `queue(queue<Value, Container>^ right);`  
  
 Tworzy opakowana kontener, który jest kopią `right->get_container()`. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt kolejki `*right`.  
  
 Konstruktor:  
  
 `explicit queue(container_type wrapped);`  
  
 wykorzystuje istniejący kontener *opakowane* jako kontener opakowana. Możesz użyć do utworzenia kolejki z istniejącego kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  

## <a name="reference"></a> Queue::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify back of queue and redisplay   
    Myqueue::reference ref = c1.back();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b x  
```  

## <a name="size"></a> Queue::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
 a b c  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  

## <a name="size_type"></a> Queue::size_type (STL/CLR)
Typ odległości ze znakiem między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ opisuje liczby nieujemnej wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_size_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myqueue::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size difference = 2  
```  

## <a name="to_array"></a> Queue::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_to_array.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c d  
a b c  
```  

## <a name="value_type"></a> Queue::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla parametru szablonu *wartość*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Myqueue::value_type val = c1.front();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
```  

## <a name="op_neq"></a> Operator! = (kolejki) (STL/CLR)
Kolejka nie równa się porównania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator!=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operator zwraca `!(left == right)`. Można go używać do testowania czy *po lewej stronie* nie jest taka sama jak określona *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_ne.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> operator&lt; (kolejki) (STL/CLR)
Dodaj do kolejki mniej niż porównania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator<(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Operator funkcja zwraca wartość true, jeśli, na najniższą pozycję `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->` [queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md) `() <` `right->size()` używanej do testowania czy *po lewej stronie* był zamówiony przed *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_lt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operator&lt;= (kolejki) (STL/CLR)
Mniejsze niż lub równe kolejki porównania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator<=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operator zwraca `!(right < left)`. Można go używać do testowania czy *po lewej stronie* nie są porządkowane po *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_le.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> Operator == (kolejki) (STL/CLR)
Porównanie równego kolejki.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator==(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operator zwraca wartość true, tylko wtedy, gdy sekwencje kontrolowane przez *po lewej stronie* i *prawo* tę samą długość, a dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go używać do testowania czy *po lewej stronie* jest taka sama jak określona *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_eq.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> operator&gt; (kolejki) (STL/CLR)
Kolejka jest większa niż porównania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator>(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operator zwraca `right` `<` `left`. Można go używać do testowania czy *po lewej stronie* są porządkowane po *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_gt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> operator&gt;= (kolejki) (STL/CLR)
Kolejka jest większa niż lub równe porównania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator>=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *left*  
 Po lewej stronie kontenera do porównania.  
  
 *right*  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operator zwraca `!(left < right)`. Można go używać do testowania czy *po lewej stronie* nie był zamówiony przed *prawo* po dwóch kolejek znajdują się w porównaniu element po elemencie.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_queue_operator_ge.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  