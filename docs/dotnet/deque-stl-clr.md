---
title: deque — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ec92f1fcda75c8d632ea2c5a8f66583d960c744a
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305868"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp losowy. Użyj kontenera `deque` do zarządzania sekwencję elementów wygląda jak ciągłego bloku magazynu, ale który można zwiększać i zmniejszać na końcu bez konieczności kopiowania wszelkie pozostałe elementy. W związku z tym można efektywnie zaimplementować `double-ended queue`. (Stąd nazwa.)  
  
 W polu poniżej, opis `GValue` jest taka sama jak `Value` o ile nie jest typu ref, w którym to przypadku jest `Value^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 GValue  
 Ogólny typ elementu w kontrolowanej sekwencji.  
  
 Wartość  
 Typ elementu w kontrolowanej sekwencji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  

## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[deque::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|  
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[deque::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[deque::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs umożliwiający kontenera.|  
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[deque::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[deque::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|  
|[deque::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|  
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[deque::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|  
|[deque::value_type (STL/CLR)](#value_type)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|  
|[deque::at (STL/CLR)](#at)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[deque::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|  
|[deque::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|  
|[deque::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|  
|[deque::deque (STL/CLR)](#deque)|Konstruuje obiekt kontenera.|  
|[deque::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|  
|[deque::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|  
|[deque::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|  
|[deque::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|  
|[deque::insert (STL/CLR)](#insert)|Dodaje elementy na określonej pozycji.|  
|[deque::pop_back (STL/CLR)](#pop_back)|Usuwa ostatnim elemencie.|  
|[deque::pop_front (STL/CLR)](#pop_front)|Usuwa pierwszego elementu.|  
|[deque::push_back (STL/CLR)](#push_back)|Dodaje nowy element ostatni.|  
|[deque::push_front (STL/CLR)](#push_front)|Dodaje nowy element pierwszy.|  
|[deque::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[deque::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[deque::resize (STL/CLR)](#resize)|Zmiany liczby elementów.|  
|[deque::size (STL/CLR)](#size)|Liczy liczbę elementów.|  
|[deque::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|  
|[deque::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|  
|[deque::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](#op_neq)|Określa, czy dwa `deque` obiekty nie są takie same.|  
|[deque::operator(STL/CLR)](#operator)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[operator< (deque) (STL/CLR)](#op_lt)|Określa, czy `deque` obiekt jest mniejszy niż innego `deque` obiektu.|  
|[operator<= (deque) (STL/CLR)](#op_lteq)|Określa, czy `deque` obiekt jest mniejszy niż lub równy do innego `deque` obiektu.|  
|[operator= (deque) (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|  
|[operator== (deque) (STL/CLR)](#op_eq)|Określa, czy `deque` obiekt jest taki sam do innego `deque` obiektu.|  
|[operator> (deque) (STL/CLR)](#op_gt)|Określa, czy `deque` obiekt jest większy niż innego `deque` obiektu.|  
|[operator>= (deque) (STL/CLR)](#op_gteq)|Określa, czy `deque` obiektu jest większa lub równa innej `deque` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|<xref:System.Collections.Generic.IList%601>|Obsługa uporządkowanej grupę elementów typu.|  
|IDeque < wartość\>|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą składowanych tablica dojść, które określają bloków `Value` elementów. Tablica rozwoju na żądanie. Rozwój występuje w taki sposób, że koszt dołączanie lub dodanie nowego elementu jest stałą czasu, a nie pozostałe elementy są zakłóceń. Można również usunąć element na końcu w czasie stałej i bez zakłóceń pozostałe elementy. W związku z tym deque — są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md) lub klasy szablonu [stosu (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `deque` obiekt obsługuje dostęp losowy Iteratory, co oznacza, że można odwołać się do elementu bezpośrednio podane położenia numeryczne, licząc od zera dla pierwszego elementu (frontonu), aby [deque::size (STL/CLR)](#size) `() - 1` dla ostatniego elementu (wstecz). Oznacza to również, że deque — są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator deque — przechowuje dojście do jego obiektu skojarzone deque — wraz z odchylenia ustanowi elementu. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Jest obliczana element deque — `not` zawsze taki sam, jak jego położenie. Pierwszy element wstawiony ma odchylenia zero, następnym elementem dołączany odchylenia 1, ale następnego elementu prepended skonfigurowano odchylenia -1.  
  
 Wstawianie lub wymazywanie elementów na końcu nie `not` alter wartość elementu przechowywanych na wszystkie prawidłowe odchylenia. Wstawianie lub wymazywanie elementu wewnętrzne, jednak `can` zmienić wartości elementu przechowywane w danym odchylenia, więc wartość wskazywany przez iteratora można także zmienić. (Kontener może być konieczne skopiuj elementy w górę lub w dół do tworzenia przerw przed wstawieniem lub do wypełnienia dziury po wymazywania). Niemniej jednak iteratora deque — pozostaje ważny tak długo, jak jego odchylenia wyznacza prawidłowego elementu. Ponadto prawidłowy iteratora pozostaje dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak jego odchylenia nie jest równa odchylenia dla zwrócony przez iterator `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
 
## <a name="member-definitions"></a>Definicje elementu członkowskiego

## <a name="assign"></a> deque::ASSIGN (STL/CLR)
Zamienia wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Wyliczenie do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Zamienia pierwszy funkcji członkowskiej kontrolowanej sekwencji powtórzenia `count` elementy wartości `val`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających taką samą wartość.  
  
 Jeśli `InIt` jest typu integer, drugi funkcji członkowskiej działa tak samo jak `assign((size_type)first, (value_type)last)`. W przeciwnym razie zastępuje kontrolowanej sekwencji z sekwencją [`first`, `last`). Umożliwia ona upewnij kontrolowanej sekwencji kopii w innej sekwencji.  
  
 Trzeci funkcji członkowskiej zastępuje kontrolowanej sekwencji sekwencji wskazywany przez moduł wyliczający `right`. Umożliwia ona utworzyć kopię sekwencji opisanego przez moduł wyliczający kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_assign.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  

## <a name="at"></a> deque::AT (STL/CLR)
Uzyskuje dostęp do elementu w określonej pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>Parametry  
 POS  
 Pozycja elementu, aby uzyskać dostęp.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwołanie do elementu w kontrolowanej sekwencji na pozycji `pos`. Służy do odczytu lub zapisu elementu, którego pozycja znasz.  
  
### <a name="example"></a>Przykład  
  
```cpp
// cliext_deque_at.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  
  
## <a name="back"></a> deque::back (STL/CLR)
Uzyskuje dostęp do ostatniego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwołanie do ostatniego elementu w kontrolowanej sekwencji musi być niepusta. Umożliwia ona dostęp do ostatniego elementu, gdy wiesz, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
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
  
## <a name="back_item"></a> deque::back_item (STL/CLR)
Uzyskuje dostęp do ostatniego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Uwagi  
 Właściwość uzyskuje dostęp do ostatniego elementu w kontrolowanej sekwencji musi być niepusta. Możesz użyć do odczytu lub zapisu ostatniego elementu, gdy wiesz, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_back_item.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
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
  
## <a name="begin"></a> deque::BEGIN (STL/CLR)
Określa początek kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dostępie swobodnym, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub bezpośrednio po zakończeniu pustej sekwencji. Służy do uzyskania iterację wyznacza `current` początku kontrolowanej sekwencji, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_begin.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="clear"></a> deque::Clear (STL/CLR)
Usuwa wszystkie elementy.  
  
### <a name="syntax"></a>Składnia  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje funkcję elementu członkowskiego [deque::erase (STL/CLR)](#erase) `(` [deque::begin (STL/CLR)](#begin) `(),` [deque::end (STL/CLR)](#end) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_clear.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
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

## <a name="const_iterator"></a> deque::const_iterator (STL/CLR)
Typ iteratora stałego dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T2` który może służyć jako stałej iteratora dostępie swobodnym w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_const_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="const_reference"></a> deque::const_reference (STL/CLR)
Typ stałego odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano stałej odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_const_reference.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::deque<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="const_reverse_iterator"></a> deque::const_reverse_iterator (STL/CLR)
Typ stałej iteratora wstecznego w kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T4` który może służyć jako stałej iteratora wstecznego w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_deque_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="deque"></a> deque::deque (STL/CLR)
Konstruuje obiekt kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Obiekt lub zakresu do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `deque();`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji.  
  
 Konstruktor:  
  
 `deque(deque<Value>% right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right.begin()`, `right.end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt deque — `right`. Aby uzyskać więcej informacji dotyczących Iteratory, zobacz [deque::begin (STL/CLR)](#begin) i [deque::end (STL/CLR)](#end).  
  
 Konstruktor:  
  
 `deque(deque<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right->begin()`, `right->end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt deque —, których obsługa jest `right`.  
  
 Konstruktor:  
  
 `explicit deque(size_type count);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `value_type()`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających wartość domyślną.  
  
 Konstruktor:  
  
 `deque(size_type count, value_type val);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `val`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających taką samą wartość.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`). Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji.  
  
 Konstruktor:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="difference_type"></a> deque::difference_type (STL/CLR)
Typy podpisane odległość między dwoma elementami.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczba podpisanego elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_deque_difference_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::deque<wchar_t>::difference_type diff = 0;   
    for (cliext::deque<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::deque<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  
  
## <a name="empty"></a> deque::EMPTY (STL/CLR)
Sprawdza, czy nie ma żadnych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wartość true dla pustego kontrolowanej sekwencji. Jest to równoważne [deque::size (STL/CLR)](#size)`() == 0`. Można użyć do sprawdzenia, czy deque — jest pusta.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_empty.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
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

## <a name="end"></a> deque::end (STL/CLR)
Określa koniec kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dostępie swobodnym tego punkty bezpośrednio po zakończeniu kontrolowanej sekwencji. Służy do uzyskania iterację wyznacza `current` koniec kontrolowanej sekwencji, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_end.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::deque<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> deque::ERASE (STL/CLR)
Usuwa elementy z określonych pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 `first`  
 Początek zakresu, aby wymazać.  
  
 `last`  
 Koniec zakresu, aby wymazać.  
  
 `where`  
 Element, aby wymazać.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez `where`. Umożliwia ona Usuń pojedynczy element.  
  
 Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`). Można użyć do usunięcia zero lub więcej elementów ciągłe.  
  
 Zarówno członek zwracają wartość iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub [deque::end (STL/CLR)](#end) `()` , jeśli nie zawiera żadnego takiego elementu.  
  
 Podczas usuwania elementów, liczbę kopii elementu jest liniowa liczby elementów między koniec wymazywania i bliżej położonego zakończeniem sekwencji. (Podczas usuwania co najmniej jeden element na końcu sekwencji, brak kopii elementu wykonywane.)  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_erase.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::deque<wchar_t>::iterator it = c1.end();   
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

## <a name="front"></a> deque::Front (STL/CLR)
Uzyskuje dostęp do pierwszego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwołanie do pierwszego elementu w kontrolowanej sekwencji musi być niepusta. Możesz używać do odczytywania lub zapisywania pierwszego elementu, gdy wiesz, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
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

## <a name="front_item"></a> deque::front_item (STL/CLR)
Uzyskuje dostęp do pierwszego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>Uwagi  
 Właściwość uzyskuje dostęp do pierwszego elementu obiektu kontrolowanej sekwencji musi być niepusta. Możesz używać do odczytywania lub zapisywania pierwszego elementu, gdy wiesz, że istnieje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_front_item.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
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

## <a name="generic_container"></a> deque::generic_container (STL/CLR)
Typ ogólny interfejs umożliwiający kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IDeque<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano ogólny interfejs dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_generic_container.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
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

## <a name="generic_iterator"></a> deque::generic_iterator (STL/CLR)
Typ iteratora do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value> generic_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano iteratora rodzajowy, używaną z ogólnym interfejsem dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::deque<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="generic_reverse_iterator"></a> deque::generic_reverse_iterator (STL/CLR)
Typ odwrotnej iteratora do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano ogólny iteratora odwrotnej służący z ogólnym interfejsem dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::deque<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> deque::generic_value (STL/CLR)
Typ elementu do użytku ogólnego interfejs dla kontenera.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano typu obiektu `GValue` opisujący wartość elementu przechowywane do użytku ogólnego interfejs dla tej klasy kontenera szablonu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_generic_value.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::deque<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> deque::INSERT (STL/CLR)
Dodaje elementy na określonej pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Wyliczenie do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
 `where`  
 Gdzie w kontenerze, aby wstawić przed.  
  
### <a name="remarks"></a>Uwagi  
 Każdy element członkowski funkcji wstawiania przed elementem wskazywana przez `where` w kontrolowanej sekwencji sekwencję określonej przez pozostałych argumentów.  
  
 Pierwszy funkcji członkowskiej wstawia element z wartością `val` i zwracającą iterator określający nowo wstawiony element. Umożliwia ona Wstaw pojedynczy element przed miejsce wskazywany przez iteratora.  
  
 Drugi funkcji członkowskiej wstawia powtórzenia `count` elementy wartości `val`. Umożliwia ona Wstawianie zero lub więcej sąsiadujących elementów, które są wszystkie kopie tej samej wartości.  
  
 Jeśli `InIt` jest typu integer trzeci funkcji członkowskiej działa tak samo jak `insert(where, (size_type)first, (value_type)last)`. W przeciwnym razie wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej sąsiadujących elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Podczas wstawiania pojedynczy element, liczbę kopii elementu jest liniowa liczby elementów między punkt wstawiania i bliżej położonego zakończeniem sekwencji. (Podczas wstawiania co najmniej jeden element na końcu sekwencji, brak kopii elementu wykonywane.) Jeśli `InIt` jest iterację wejściowych trzeci funkcji członkowskiej skutecznie wykonuje wstawiania jednej dla każdego elementu w sekwencji. W przeciwnym razie podczas wstawiania `N` elementów, liczbę kopii elementu jest liniowa w `N` wraz z liczbą elementów między punkt wstawiania i bliżej położonego zakończeniem sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_insert.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  

## <a name="iterator"></a> deque::iterator (STL/CLR)
Typ iteratora dla kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T1` który może służyć jako iterator dostępie swobodnym w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="op_neq"></a> deque::operator! = (STL/CLR)
Deque — jest nierówne porównania.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator!=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `left`  
 Po lewej stronie kontenera do porównania.  
  
 `right`  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(left == right)`. Można go użyć do przetestowania czy `left` nie jest taka sama jak określona `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_ne.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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

## <a name="operator"></a> deque::operator(STL/CLR)
Uzyskuje dostęp do elementu w określonej pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>Parametry  
 POS  
 Pozycja elementu, aby uzyskać dostęp.  
  
### <a name="remarks"></a>Uwagi  
 Operator członkowski zwraca referene do elementu na pozycji `pos`. Umożliwia ona uzyskiwanie dostępu do elementu, którego pozycja znasz.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_sub.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="pop_back"></a> deque::pop_back (STL/CLR)
Usuwa ostatnim elemencie.  
  
### <a name="syntax"></a>Składnia  
  
```  
void pop_back();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa ostatniego elementu w kontrolowanej sekwencji musi być niepusta. Umożliwia ona skrócić czas deque — przez jeden element z tyłu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_pop_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  

## <a name="pop_front"></a> deque::pop_front (STL/CLR)
Usuwa pierwszego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void pop_front();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa pierwszego elementu obiektu kontrolowanej sekwencji musi być niepusta. Umożliwia ona skrócić czas deque — przez element jednego z przodu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_pop_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
b c  
```  
  
## <a name="push_back"></a> deque::push_back (STL/CLR)
Dodaje nowy element ostatni.  
  
### <a name="syntax"></a>Składnia  
  
```  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska wstawia element z wartością `val` na końcu kontrolowanej sekwencji. Umożliwia ona dołączyć inny element do deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_push_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="push_front"></a> deque::push_front (STL/CLR)
Dodaje nowy element pierwszy.  
  
### <a name="syntax"></a>Składnia  
  
```  
void push_front(value_type val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska wstawia element z wartością `val` na początku kontrolowanej sekwencji. Umożliwia ona dołączy innego elementu deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_push_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="rbegin"></a> deque::rbegin (STL/CLR)
Określa początek odwróconej kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora, który wyznacza ostatniego elementu w kontrolowanej sekwencji lub poza początku pustej sekwencji. W związku z tym wyznacza `beginning` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` początku kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_rbegin.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> deque::Reference (STL/CLR)
Typ odwołania do elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano odwołanie do elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_deque_reference.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::deque<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::deque<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="rend"></a> deque::rend (STL/CLR)
Określa koniec odwróconej kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora tego punktów poza początku kontrolowanej sekwencji. W związku z tym wyznacza `end` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_deque_rend.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="resize"></a> deque::Resize (STL/CLR)
Zmiany liczby elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_size  
 Nowy rozmiar kontrolowanej sekwencji.  
  
 Val  
 Wartość elementu dopełnienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie zarówno upewnij się, że [deque::size (STL/CLR)](#size) `()` odtąd zwraca `new_size`. Należy go dłużej kontrolowanej sekwencji, pierwszej funkcji Członkowskich dołącza elementy o wartości `value_type()`, podczas gdy druga funkcji członkowskiej dołącza elementy o wartości `val`. Aby kontrolowanej sekwencji krótszy, zarówno funkcje Członkowskie skutecznie wymazać ostatni element [deque::size (STL/CLR)](#size) `() -` `new_size` razy. Umożliwia ona upewnij się, że kontrolowanej sekwencji ma rozmiar `new_size`, przycinanie lub dopełnienie bieżącego kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse_iterator"></a> deque::reverse_iterator (STL/CLR)
Typ odwrotnej iteratora w kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu nieokreślonego typu `T3` który może służyć jako odwrotnej iteratora w kontrolowanej sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// cliext_deque_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
 
## <a name="size"></a> deque::size (STL/CLR)
Liczy liczbę elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość kontrolowanej sekwencji. Można użyć do określenia liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli wszystkie najważniejsze informacje dotyczące tego, czy sekwencja ma rozmiar różną od zera, zobacz [deque::empty (STL/CLR)](#empty)`()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_size.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
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

## <a name="size_type"></a> deque::size_type (STL/CLR)
Typ podpisem odległość między dwoma elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano liczbą nieujemną elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_size_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> deque::swap (STL/CLR)
Zamienia zawartości dwóch kontenerów.  
  
### <a name="syntax"></a>Składnia  
  
```  
void swap(deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do wymiany zawartości z.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia kontrolowanej sekwencji między `*this` i `right`. Robi to w czasie stałej i zgłasza żadnych wyjątków. Możesz używać go jako szybko do wymiany zawartości dwóch kontenerów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_swap.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> c2(5, L'x');   
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

## <a name="to_array"></a> deque::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona uzyskać kopię kontrolowanej sekwencji w postaci tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_to_array.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
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
  
## <a name="value_type"></a> deque::value_type (STL/CLR)
Typ elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Value`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_value_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::deque<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::deque<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_lt"></a> operator&lt; (deque —) (STL/CLR)
Deque — mniej niż porównania.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator<(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Operator funkcja zwraca wartość true, jeśli, dla najniżej `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używanej do testowania czy `left` jest umieszczane przed `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_lt.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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

## <a name="op_lteq"></a> operator&lt;= (deque —) (STL/CLR)
Deque — mniejsze niż lub równa porównania.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator<=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(right < left)`. Można go użyć do przetestowania czy `left` porządkowania nie po `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_le.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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

## <a name="op_as"></a> Operator = (deque —) (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
deque<Value>% operator=(deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień kontrolowanej sekwencji kopię w kontrolowanej sekwencji `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_as.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
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
  
## <a name="op_eq"></a> Operator == (deque —) (STL/CLR)
Deque — porównanie takie same.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator==(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operatora zwraca wartość true, tylko wtedy, gdy w sekwencji, które są kontrolowane przez `left` i `right` ma taką samą długość i dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go użyć do przetestowania czy `left` jest taka sama jak określona `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_eq.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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

## <a name="op_gt"></a> operator&gt; (deque —) (STL/CLR)
Deque — jest większa niż porównania.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator>(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operatora `right` `<` `left`. Można go użyć do przetestowania czy `left` porządkowania po `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_gt.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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

## <a name="op_gteq"></a> operator&gt;= (deque —) (STL/CLR)
Deque — większa niż lub równa porównania.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator>=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(left` `<` `right)`. Można go użyć do przetestowania czy `left` nie jest umieszczane przed `right` po dwóch deques są porównaniu elementu przez element.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_operator_ge.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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
 