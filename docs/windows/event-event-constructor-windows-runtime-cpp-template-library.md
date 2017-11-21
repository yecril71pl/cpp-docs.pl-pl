---
title: "Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs: C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88fafd4bb345d8e70f84aa87c04592e91703b5c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Event — klasa (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)