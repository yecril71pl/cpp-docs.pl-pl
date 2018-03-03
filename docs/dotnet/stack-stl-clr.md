---
title: stos (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::stack
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7f6d9eac97fa1907a0901c725645f29dcdd5d9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp w ostatniej FIFO. Użyj karty kontenera `stack` Zarządzanie kontenerem podstawowej jako stosu rozwijana wypychania.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `Value` o ile nie jest typu ref, w którym to przypadku jest `Value^`. Podobnie `GContainer` jest taka sama jak `Container` o ile nie jest typu ref, w którym to przypadku jest `Container^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Wartość  
 Typ elementu w kontrolowanej sekwencji.  
  
 Kontener  
 Typ podstawowy kontenera.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|Typ podstawowy kontenera.|  
|[stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający karty kontenera.|  
|[stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|Typ elementu ogólnego interfejsu dla karty kontenera.|  
|[stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|Zamienia wszystkie elementy.|  
|[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|Uzyskuje dostęp do podstawowych kontenera.|  
|[stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|Usuwa ostatnim elemencie.|  
|[stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|Dodaje nowy element ostatni.|  
|[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|Liczy liczbę elementów.|  
|[stack::stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|Określa, czy `stack` obiekt nie jest równa innej `stack` obiektu.|  
|[operator< (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|Określa, czy `stack` obiekt jest mniejszy niż innego `stack` obiektu.|  
|[operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|Określa, czy `stack` obiekt jest mniejszy niż lub równy do innego `stack` obiektu.|  
|[operator== (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|Określa, czy `stack` obiekt jest taki sam do innego `stack` obiektu.|  
|[operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|Określa, czy `stack` obiekt jest większy niż innego `stack` obiektu.|  
|[operator>= (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|Określa, czy `stack` obiektu jest większa lub równa innej `stack` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|IStack\<wartość, kontener >|Obsługa karty Ogólne kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą podstawowej kontenera, typu obiektu `Container`, który przechowuje `Value` elementów i rozwoju na żądanie. Obiekt ogranicza dostęp do wypychania i wyświetlanie tylko ostatni element, implementacja kolejki w ostatniej FIFO (znanej także jako kolejka LIFO, lub stos).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/stack >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)