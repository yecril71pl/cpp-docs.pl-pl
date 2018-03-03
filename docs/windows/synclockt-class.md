---
title: "Synclockt — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f3a9794f7b00a2029f6706db3a846ba127a4d5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="synclockt-class"></a>SyncLockT — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `SyncTraits`  
 Typ, który może przejąć na własność zasobu.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje typ, które może podjąć wyłącznych lub własność zasobu udostępnionego.  
  
 Synclockt — klasa jest używana na przykład pomagających w realizacji [srwlock —](../windows/srwlock-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT, konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicjuje nowe wystąpienie klasy SyncLockT.|  
|[SyncLockT::~SyncLockT, destruktor](../windows/synclockt-tilde-synclockt-destructor.md)|Deinitializes wystąpienia klasy SyncLockT.|  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockT::SyncLockT, konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicjuje nowe wystąpienie klasy SyncLockT.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockT::IsLocked, metoda](../windows/synclockt-islocked-method.md)|Wskazuje, czy bieżący obiekt SyncLockT jest właścicielem zasobu; Obiekt SyncLockT jest *zablokowany*.|  
|[SyncLockT::Unlock, metoda](../windows/synclockt-unlock-method.md)|Zwalnia kontrolę nad zasobem posiadanych przez bieżący obiekt SyncLockT, jeśli istnieją.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SyncLockT::sync_, składowa danych](../windows/synclockt-sync-data-member.md)|Przechowuje podstawowej zasobu reprezentowanego przez synclockt — klasa.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SyncLockT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock, klasa](../windows/srwlock-class.md)