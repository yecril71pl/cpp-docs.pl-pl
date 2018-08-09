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
ms.openlocfilehash: 23881f2065276aa7ae7b6ee95b5449abb07dd2de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641956"
---
# <a name="srwlock-class"></a>SRWLock — Klasa
Reprezentuje kieszeń czytnika/blokadę.  
  
## <a name="syntax"></a>Składnia  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Uwagi  
 Cienki czytnika/blokadę służy do synchronizowania dostępu w wątkach do obiektu lub zasobu. Aby uzyskać więcej informacji, zobacz [funkcji synchronizacji](http://msdn.microsoft.com/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|||  
|-|-|  
|`SyncLockExclusive`|Synonim dla **SRWLock** obiekt, który jest uzyskiwany w trybie wyłączności.|  
|`SyncLockShared`|Synonim dla **SRWLock** obiekt, który jest uzyskiwany w trybie udostępniania.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::SRWLock, konstruktor](../windows/srwlock-srwlock-constructor.md)|Inicjuje nowe wystąpienie klasy **SRWLock** klasy.|  
|[SRWLock::~SRWLock, destruktor](../windows/srwlock-tilde-srwlock-destructor.md)|Wyłącza wystąpienie **SRWLock** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::LockExclusive, metoda](../windows/srwlock-lockexclusive-method.md)|Uzyskuje **SRWLock** obiektu w trybie wyłączności.|  
|[SRWLock::LockShared, metoda](../windows/srwlock-lockshared-method.md)|Uzyskuje **SRWLock** obiektu w tryb udostępniania.|  
|[SRWLock::TryLockExclusive, metoda](../windows/srwlock-trylockexclusive-method.md)|Próbuje pobrać **SRWLock** obiektu w trybie wyłączności dla bieżącej lub określonej **SRWLock** obiektu.|  
|[SRWLock::TryLockShared, metoda](../windows/srwlock-trylockshared-method.md)|Próbuje pobrać **SRWLock** obiektu w tryb udostępniania dla bieżącej lub określonej **SRWLock** obiektu.|  
  
### <a name="protected-data-member"></a>Element członkowski danych chronionych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLock::SRWLock_, składowa danych](../windows/srwlock-srwlock-data-member.md)|Zawiera podstawowe zmienną blokady dla bieżącego **SRWLock** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)