---
title: kolejki (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5b91a2556a93f3cd74a24ea57306d70f2cbdb41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp w pierwszym FIFO. Użyj karty kontenera `queue` Zarządzanie kontenerem podstawowej jako kolejki.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `Value` o ile nie jest typu ref, w którym to przypadku jest `Value^`. Podobnie `GContainer` jest taka sama jak `Container` o ile nie jest typu ref, w którym to przypadku jest `Container^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|Typ podstawowy kontenera.|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający karty kontenera.|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|Typ elementu ogólnego interfejsu dla karty kontenera.|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|Typ odległości ze znakiem między dwoma elementami.|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|Zamienia wszystkie elementy.|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|Uzyskuje dostęp do podstawowych kontenera.|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|Usuwa pierwszego elementu.|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|Dodaje nowy element ostatni.|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|Liczy liczbę elementów.|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|Uzyskuje dostęp do ostatniego elementu.|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|Uzyskuje dostęp do pierwszego elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|Określa, czy `queue` obiekt nie jest równa innej `queue` obiektu.|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|Określa, czy `queue` obiekt jest mniejszy niż innego `queue` obiektu.|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Określa, czy `queue` obiekt jest mniejszy niż lub równy do innego `queue` obiektu.|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|Określa, czy `queue` obiekt jest taki sam do innego `queue` obiektu.|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|Określa, czy `queue` obiekt jest większy niż innego `queue` obiektu.|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Określa, czy `queue` obiektu jest większa lub równa innej `queue` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|IQueue\<wartość, kontener >|Obsługa karty Ogólne kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą podstawowej kontenera, typu obiektu `Container`, który przechowuje `Value` elementów i rozwoju na żądanie. Obiekt ogranicza dostęp do wypychania tylko pierwszy element i wyświetlanie ostatnim elementem, implementacja FIFO w pierwszej kolejki (znanej także jako kolejce FIFO lub po prostu kolejki).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [stos (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)