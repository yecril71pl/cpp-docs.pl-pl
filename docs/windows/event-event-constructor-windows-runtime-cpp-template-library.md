---
title: Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c2683d2e1875e7d68d27f7bde515b7a4ca70da0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649731"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)
Inicjuje nowe wystąpienie klasy **zdarzeń** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Obsłuż to zdarzenie. Domyślnie *h* jest inicjowany do **nullptr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)