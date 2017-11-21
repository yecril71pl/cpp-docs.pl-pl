---
title: "Module::UnregisterWinRTObject — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs: C++
helpviewer_keywords: UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c5f1fe4da0d9c0699ab7205ad7823ca8d506dd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject — Metoda
Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego systemu Windows, dzięki czemu inne aplikacje nie mogą łączyć się je.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `cookie`  
 Wskaźnik do wartości określające obiekt klasy, którego rejestracja ma zostać odwołany.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)