---
title: "Criticalsection — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2bf6e4728bac6622f9872ab939e084b14f49ae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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