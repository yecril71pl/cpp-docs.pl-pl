---
title: "Synclockwithstatust — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b4b007acd6e6b9272a4fc7bb256d302cafeb75c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `SyncTraits`  
 Typ, które może podjąć wyłącznych lub własność zasobu udostępnionego.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje typ, które może podjąć wyłącznych lub własność zasobu udostępnionego.  
  
 Synclockwithstatust — klasa jest używana do zaimplementowania [obiektu Mutex](../windows/mutex-class1.md) i [semafora](../windows/semaphore-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT, konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy synclockwithstatust — klasa.|  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT, konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy synclockwithstatust — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus, metoda](../windows/synclockwithstatust-getstatus-method.md)|Pobiera bieżący obiekt synclockwithstatust — stan oczekiwania.|  
|[SyncLockWithStatusT::IsLocked, metoda](../windows/synclockwithstatust-islocked-method.md)|Wskazuje, czy bieżący obiekt synclockwithstatust — jest właścicielem zasobu; synclockwithstatust — obiektu jest *zablokowany*.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockWithStatusT::status_, składowa danych](../windows/synclockwithstatust-status-data-member.md)|Blokad wynik podstawowych oczekiwania operacji po operacji blokowania na obiekt oparte na bieżący obiekt synclockwithstatust —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)