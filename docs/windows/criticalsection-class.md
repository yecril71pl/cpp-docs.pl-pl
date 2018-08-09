---
title: Criticalsection — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b65ded3ae56eb1d57bad771a8875cce4948d2953
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642097"
---
# <a name="criticalsection-class"></a>CriticalSection — Klasa
Reprezentuje obiekt sekcję krytyczną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class CriticalSection;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructor"></a>Konstruktor  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::CriticalSection, konstruktor](../windows/criticalsection-criticalsection-constructor.md)|Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko pojedynczego procesu.|  
|[CriticalSection::~CriticalSection, destruktor](../windows/criticalsection-tilde-criticalsection-destructor.md)|Wyłącza i niszczy bieżącego **CriticalSection** obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::TryLock, metoda](../windows/criticalsection-trylock-method.md)|Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność sekcję krytyczną.|  
|[CriticalSection::Lock, metoda](../windows/criticalsection-lock-method.md)|Czeka na własność obiektu określona sekcja krytycznego. Funkcja zwróci, jeśli wątek wywołujący udzielono prawa własności.|  
|[CriticalSection::IsValid, metoda](../windows/criticalsection-isvalid-method.md)|Wskazuje, czy bieżąca sekcja krytycznego jest prawidłowa.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::cs_, składowa danych](../windows/criticalsection-cs-data-member.md)|Deklaruje element członkowski danych sekcję krytyczną.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)