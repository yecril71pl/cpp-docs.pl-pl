---
title: Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9a63e7ddbf2528b78eac7761bbcf4891f31cc886
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)
Inicjuje nowe wystąpienie klasy zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Dojście do zdarzenia. Domyślnie `h` jest ustawiana na `nullptr`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)