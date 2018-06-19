---
title: Wektor (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de5d09d569933dc06666ed2008081703d59c1564
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172641"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp losowy. Użyj kontenera `vector` do zarządzania sekwencję elementów jako ciągłego bloku pamięci masowej. Blok jest implementowany jako tablicę, która rozwoju na żądanie.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `Value` o ile nie jest typu ref, w którym to przypadku jest `Value^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Wartość  
 Typ elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[vector::reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|Zamienia wszystkie elementy.|  
|[vector::at (STL/CLR)](../dotnet/vector-at-stl-clr.md)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[vector::capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|Informuje o rozmiarze Magazyn przydzielony do kontenera.|  
|[vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
|[vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|Dodaje elementy na określonej pozycji.|  
|[vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|Usuwa ostatnim elemencie.|  
|[vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|Dodaje nowy element ostatni.|  
|[vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|Zapewnia wzrostu minimalnej pojemności dla kontenera.|  
|[vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|Zmiany liczby elementów.|  
|[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|Liczy liczbę elementów.|  
|[vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[vector::vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|Konstruuje obiekt kontenera.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[vector::operator(STL/CLR)](../dotnet/vector-operator-stl-clr.md)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[operator!= (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|Określa, czy `vector` obiekt nie jest równa innej `vector` obiektu.|  
|[operator< (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|Określa, czy `vector` obiekt jest mniejszy niż innego `vector` obiektu.|  
|[operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|Określa, czy `vector` obiekt jest mniejszy niż lub równy do innego `vector` obiektu.|  
|[operator== (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|Określa, czy `vector` obiekt jest taki sam do innego `vector` obiektu.|  
|[operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|Określa, czy `vector` obiekt jest większy niż innego `vector` obiektu.|  
|[operator>= (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|Określa, czy `vector` obiektu jest większa lub równa innej `vector` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|<xref:System.Collections.Generic.IList%601>|Obsługa uporządkowanej grupę elementów typu.|  
|IVector < wartość\>|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą składowanych tablicę `Value` elementów, które rozwoju na żądanie. Rozwój występuje w taki sposób, że koszt Dołączanie nowego elementu jest amortyzowanego stałej czasu. Innymi słowy kosztów Dodawanie elementów na końcu nie zwiększa, średnio, ponieważ długość większa pobiera kontrolowanej sekwencji. W związku z tym wektora są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [stosu (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `vector` obsługuje dostęp losowy Iteratory, co oznacza, że można odwołać się do elementu bezpośrednio podanej pozycji numeryczny licząc od zera dla pierwszego elementu (z przodu), aby `size() - 1` ostatniego elementu (wstecz). Oznacza to również, że wektora są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator wektor przechowuje dojście do jego obiektu skojarzone wektora, wraz z odchylenia ustanowi elementu. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Różnica elementu vector jest taka sama jak jego położenie.  
  
 Wstawiania lub usuwania elementów można zmienić wartości elementu przechowywane na określonej pozycji, aby również zmienić wartość wskazywany przez iteratora. (Kontener może być konieczne skopiuj elementy w górę lub w dół do tworzenia przerw przed wstawieniem lub do wypełnienia dziury po wymazywania). Niemniej jednak iteratora wektor pozostaje ważny tak długo, jak jego odchylenia znajduje się w zakresie `[0, size()]`. Ponadto prawidłowy iteratora pozostaje dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak jego odchylenia nie jest równa `size()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, kontener dojść nie niszczy swoich elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [stos (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)