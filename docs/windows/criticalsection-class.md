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
ms.openlocfilehash: 8b5eda8fb22f72bd1f50801f9993b9bd7a864d35
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871513"
---
# <a name="criticalsection-class"></a>CriticalSection — Klasa
Reprezentuje obiekt sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CriticalSection;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructor"></a>Konstruktor  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::CriticalSection, konstruktor](../windows/criticalsection-criticalsection-constructor.md)|Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko jednego procesu.|  
|[CriticalSection::~CriticalSection, destruktor](../windows/criticalsection-tilde-criticalsection-destructor.md)|Deinitializes i niszczy bieżący obiekt criticalsection —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::TryLock, metoda](../windows/criticalsection-trylock-method.md)|Próbuje wpisz sekcja krytyczna bez blokowania. Jeśli połączenie zostanie nawiązane, wątek wywołujący przejmuje sekcja krytyczna.|  
|[CriticalSection::Lock, metoda](../windows/criticalsection-lock-method.md)|Czeka na prawo własności obiektu określona sekcja krytyczna. Funkcja zwraca, gdy wątek wywołujący jest własność.|  
|[CriticalSection::IsValid, metoda](../windows/criticalsection-isvalid-method.md)|Wskazuje, czy bieżąca sekcja krytyczna jest nieprawidłowy.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection::cs_, składowa danych](../windows/criticalsection-cs-data-member.md)|Deklaruje element członkowski danych sekcja krytyczna.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)