---
title: "Srwlock — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs: C++
helpviewer_keywords: SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1325a089739b3820009aa239f56805264dbb6b83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="srwlock-class"></a>SRWLock — Klasa
Reprezentuje cienki czytnika/blokadę.  
  
## <a name="syntax"></a>Składnia  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Uwagi  
 Cienki czytnika/blokadę jest używane do synchronizowania dostępu pomiędzy wątkami do obiektu lub zasobu. Aby uzyskać więcej informacji, zobacz [funkcje synchronizacji](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|||  
|-|-|  
|**SyncLockExclusive**|Synonim dla obiekt srwlock —, która jest uzyskiwana w trybie wyłączności.|  
|**SyncLockShared**|Synonim dla obiekt srwlock — są uzyskiwane w trybie udostępniania.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::SRWLock, konstruktor](../windows/srwlock-srwlock-constructor.md)|Inicjuje nowe wystąpienie klasy srwlock —.|  
|[SRWLock::~SRWLock, destruktor](../windows/srwlock-tilde-srwlock-destructor.md)|Deinitializes wystąpienia klasy srwlock —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::LockExclusive, metoda](../windows/srwlock-lockexclusive-method.md)|Uzyskuje obiekt srwlock — w trybie wyłączności.|  
|[SRWLock::LockShared, metoda](../windows/srwlock-lockshared-method.md)|Uzyskuje obiekt srwlock — w trybie udostępniania.|  
|[SRWLock::TryLockExclusive, metoda](../windows/srwlock-trylockexclusive-method.md)|Próby uzyskania obiektu srwlock — w trybie wyłączności dla bieżącego lub określonego obiektu srwlock —.|  
|[SRWLock::TryLockShared, metoda](../windows/srwlock-trylockshared-method.md)|Próby uzyskania obiektu srwlock — w trybie udostępniania dla bieżącego lub określonego obiektu srwlock —.|  
  
### <a name="protected-data-member"></a>Element członkowski chronionych danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::SRWLock_, składowa danych](../windows/srwlock-srwlock-data-member.md)|Zawiera zmienną podstawowej blokady dla bieżącego obiektu srwlock —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)