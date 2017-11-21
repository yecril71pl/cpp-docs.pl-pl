---
title: "Microsoft::wrl:: wrappers — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers
dev_langs: C++
helpviewer_keywords: Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7390f68d7bc7c7856d1fef35ba1fb180b8341559
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Criticalsection — klasa](../windows/criticalsection-class.md)|Reprezentuje obiekt sekcja krytyczna.|  
|[Event — klasa (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)|Reprezentuje zdarzenie.|  
|[Handlet — klasa](../windows/handlet-class.md)|Reprezentuje uchwyt do obiektu.|  
|[Hstring — klasa](../windows/hstring-class.md)|Zapewnia obsługę manipulowanie HSTRING uchwytów.|  
|[Hstringreference — klasa](../windows/hstringreference-class.md)|Reprezentuje wartość HSTRING utworzona na podstawie istniejących parametrów.|  
|[Mutex — klasa](../windows/mutex-class1.md)|Reprezentuje obiekt synchronizacji wyłącznie kontrolujące zasobu udostępnionego.|  
|[Roinitializewrapper — klasa](../windows/roinitializewrapper-class.md)|Inicjuje środowiska uruchomieniowego systemu Windows.|  
|[Klasa semaforu](../windows/semaphore-class.md)|Reprezentuje obiekt synchronizacji, która kontroluje, czy obsługują ograniczoną liczbę użytkowników zasobu udostępnionego.|  
|[Srwlock — klasa](../windows/srwlock-class.md)|Reprezentuje cienki czytnika/blokadę.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)