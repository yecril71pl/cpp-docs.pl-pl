---
title: "Microsoft::wrl:: wrappers — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7633bcd784fa7b9b5f7255e25e8ddc52c5b93db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers — Przestrzeń nazw
Określa typy otoki zasobów nabycia jest inicjowania (RAII), upraszczające Zarządzanie okresem istnienia obiektów, ciągi i uchwytów.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="typedefs"></a>Typedefs  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSection, klasa](../windows/criticalsection-class.md)|Reprezentuje obiekt sekcja krytyczna.|  
|[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)|Reprezentuje zdarzenie.|  
|[HandleT, klasa](../windows/handlet-class.md)|Reprezentuje uchwyt do obiektu.|  
|[HString, klasa](../windows/hstring-class.md)|Zapewnia obsługę manipulowanie HSTRING uchwytów.|  
|[HStringReference, klasa](../windows/hstringreference-class.md)|Reprezentuje wartość HSTRING utworzona na podstawie istniejących parametrów.|  
|[Mutex — klasa](../windows/mutex-class1.md)|Reprezentuje obiekt synchronizacji wyłącznie kontrolujące zasobu udostępnionego.|  
|[RoInitializeWrapper, klasa](../windows/roinitializewrapper-class.md)|Inicjuje środowiska uruchomieniowego systemu Windows.|  
|[Semaphore, klasa](../windows/semaphore-class.md)|Reprezentuje obiekt synchronizacji, która kontroluje, czy obsługują ograniczoną liczbę użytkowników zasobu udostępnionego.|  
|[SRWLock, klasa](../windows/srwlock-class.md)|Reprezentuje cienki czytnika/blokadę.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)