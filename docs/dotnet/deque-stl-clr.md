---
title: deque — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 11436466dadf4b06e604af6e2b5150a22c4ed241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111149"
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
  
#### <a name="parameters"></a>Parametry  
 GValue  
 Ogólny typ elementu w kontrolowanej sekwencji.  
  
 Wartość  
 Typ elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|Zamienia wszystkie elementy.|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|Dodaje elementy na określonej pozycji.|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|Usuwa ostatnim elemencie.|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|Usuwa pierwszego elementu.|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|Dodaje nowy element ostatni.|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|Dodaje nowy element pierwszy.|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|Zmiany liczby elementów.|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|Liczy liczbę elementów.|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|Określa, czy dwa `deque` obiekty nie są takie same.|  
|[deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)|Uzyskuje dostęp do elementu w określonej pozycji.|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|Określa, czy `deque` obiekt jest mniejszy niż innego `deque` obiektu.|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|Określa, czy `deque` obiekt jest mniejszy niż lub równy do innego `deque` obiektu.|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|Określa, czy `deque` obiekt jest taki sam do innego `deque` obiektu.|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|Określa, czy `deque` obiekt jest większy niż innego `deque` obiektu.|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|Określa, czy `deque` obiektu jest większa lub równa innej `deque` obiektu.|  
  
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
  
 A `deque` obiekt obsługuje dostęp losowy Iteratory, co oznacza, że można odwołać się do elementu bezpośrednio podane położenia numeryczne, licząc od zera dla pierwszego elementu (frontonu), aby [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1` dla ostatniego elementu (wstecz). Oznacza to również, że deque — są odpowiednimi kandydatami podstawowej kontenera dla szablonu klasy [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator deque — przechowuje dojście do jego obiektu skojarzone deque — wraz z odchylenia ustanowi elementu. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Jest obliczana element deque — `not` zawsze taki sam, jak jego położenie. Pierwszy element wstawiony ma odchylenia zero, następnym elementem dołączany odchylenia 1, ale następnego elementu prepended skonfigurowano odchylenia -1.  
  
 Wstawianie lub wymazywanie elementów na końcu nie `not` alter wartość elementu przechowywanych na wszystkie prawidłowe odchylenia. Wstawianie lub wymazywanie elementu wewnętrzne, jednak `can` zmienić wartości elementu przechowywane w danym odchylenia, więc wartość wskazywany przez iteratora można także zmienić. (Kontener może być konieczne skopiuj elementy w górę lub w dół do tworzenia przerw przed wstawieniem lub do wypełnienia dziury po wymazywania). Niemniej jednak iteratora deque — pozostaje ważny tak długo, jak jego odchylenia wyznacza prawidłowego elementu. Ponadto prawidłowy iteratora pozostaje dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak jego odchylenia nie jest równa odchylenia dla zwrócony przez iterator `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [stos (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)