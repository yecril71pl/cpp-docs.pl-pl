---
title: Lista (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list
dev_langs: C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 991b72b312c8ad1b36a9a401a6452ec36ea25d6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="list-stlclr"></a>list (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `list` Zarządzanie sekwencję elementów jako dwukierunkowy połączonej listy węzłów, w każdym przechowywania jeden element.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `Value` o ile nie jest typu ref, w którym to przypadku jest `Value^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Wartość  
 Typ elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[list::Reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[list::ASSIGN (STL/CLR)](../dotnet/list-assign-stl-clr.md)|Zamienia wszystkie elementy.|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[list::BEGIN (STL/CLR)](../dotnet/list-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[list::Clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[list::EMPTY (STL/CLR)](../dotnet/list-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[list::ERASE (STL/CLR)](../dotnet/list-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[list::Front (STL/CLR)](../dotnet/list-front-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
|[list::INSERT (STL/CLR)](../dotnet/list-insert-stl-clr.md)|Dodaje elementy na określonej pozycji.|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|Scala dwie uporządkowane kontrolowanej sekwencji.|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|Usuwa ostatnim elemencie.|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|Usuwa pierwszego elementu.|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|Dodaje nowy element ostatni.|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|Dodaje nowy element pierwszy.|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[list::Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|Usuwa element z określoną wartością.|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|Usuwa elementy przekazujące określonego testu.|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[list::Resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|Zmiany liczby elementów.|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|Odwraca kontrolowanej sekwencji.|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|Liczy liczbę elementów.|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|Ustala kolejność kontrolowanej sekwencji.|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|Restitches łącza między węzłami.|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[list::Unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|Usuwa elementy sąsiednie przekazujące określonego testu.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[list::operator = (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[Operator! = (lista) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|Określa, czy `list` obiekt nie jest równa innej `list` obiektu.|  
|[Operator < (lista) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|Określa, czy `list` obiekt jest mniejszy niż innego `list` obiektu.|  
|[Operator < = (lista) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|Określa, czy `list` obiekt jest mniejszy niż lub równy do innego `list` obiektu.|  
|[Operator == (lista) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|Określa, czy `list` obiekt jest taki sam do innego `list` obiektu.|  
|[operator > (Wyświetl) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|Określa, czy `list` obiekt jest większy niż innego `list` obiektu.|  
|[operator > = (lista) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|Określa, czy `list` obiektu jest większa lub równa innej `list` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|IList\<wartość >|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu w sekwencji, które kontroluje jako poszczególne węzły na liście łącze dwukierunkowego. Go Rozmieszcza elementy, zmieniając łącza między węzłami, nigdy nie, kopiując zawartość z jednego węzła do innego. Oznacza to, można wstawiać i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy. W związku z tym listy są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md) lub klasy szablonu [stosu (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `list` obiekt obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora listy, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu listy bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym. Dlatego listy `not` można używać jako podstawowej kontener dla szablonu klasy [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator listy przechowuje dojścia do węzła skojarzonej listy, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Iterator listy pozostaje ważny tak długo, jak jego węzła listy skojarzonej jest skojarzony z niektórych listy. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [stos (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Odwołanie do biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)