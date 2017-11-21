---
title: "Makeallocator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAllocator
dev_langs: C++
helpviewer_keywords: MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0333dec823cb3996a9546bbfa702b3febf711a61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="makeallocator-class"></a>MakeAllocator — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Nazwa typu.  
  
 `hasWeakReferenceSupport`  
 `true`można przydzielić pamięci dla obiekt, który obsługuje słabe odwołania; `false` można przydzielić pamięci dla obiektu, który nie obsługuje słabe odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Przydziela pamięć dla klasy aktywowalnej, z lub bez obsługi słabe odwołanie.  
  
 Zastąpienie makeallocator — klasa implementacji modelu alokacji pamięci zdefiniowane przez użytkownika.  
  
 Makeallocator — zazwyczaj jest używany do chronienia przecieki pamięci, jeśli obiekt zgłasza wyjątek podczas konstruowania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Makeallocator::makeallocator — Konstruktor](../windows/makeallocator-makeallocator-constructor.md)|Inicjuje nowe wystąpienie klasy makeallocator —.|  
|[Makeallocator —:: ~ MakeAllocator — destruktor](../windows/makeallocator-tilde-makeallocator-destructor.md)|Deinitializes bieżące wystąpienie klasy makeallocator — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[MakeAllocator::Allocate — metoda](../windows/makeallocator-allocate-method.md)|Przydziela pamięć i kojarzy ją z bieżącym obiektem makeallocator —.|  
|[MakeAllocator::Detach — metoda](../windows/makeallocator-detach-method.md)|Usuwa skojarzenia pamięci przydzielonej przez [przydziel](../windows/makeallocator-allocate-method.md) metody z bieżącego obiektu makeallocator —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `MakeAllocator`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)