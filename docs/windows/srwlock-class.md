---
title: Srwlock — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec31b1469f437ff2776ed9da52fbcd7557fca8e2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891756"
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