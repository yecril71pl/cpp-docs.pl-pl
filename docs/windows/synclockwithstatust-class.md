---
title: "Synclockwithstatust — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs: C++
helpviewer_keywords: SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1d2cd87c7a77501981904686f0bea0b3c7444e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Synclockwithstatust::synclockwithstatust — Konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy synclockwithstatust — klasa.|  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Synclockwithstatust::synclockwithstatust — Konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy synclockwithstatust — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus — metoda](../windows/synclockwithstatust-getstatus-method.md)|Pobiera bieżący obiekt synclockwithstatust — stan oczekiwania.|  
|[SyncLockWithStatusT::IsLocked — metoda](../windows/synclockwithstatust-islocked-method.md)|Wskazuje, czy bieżący obiekt synclockwithstatust — jest właścicielem zasobu; synclockwithstatust — obiektu jest *zablokowany*.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Synclockwithstatust::status_ — członek danych](../windows/synclockwithstatust-status-data-member.md)|Blokad wynik podstawowych oczekiwania operacji po operacji blokowania na obiekt oparte na bieżący obiekt synclockwithstatust —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)