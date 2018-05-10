---
title: Synclockt — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e05a1be5d84db52573d3c3235936ecf82dde5894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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