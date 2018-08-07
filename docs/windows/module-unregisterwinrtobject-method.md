---
title: Module::UnregisterWinRTObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5bf681acc485b08448fcb4e936ca1096a8137384
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607475"
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject — Metoda
Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego Windows, tak aby inne aplikacje nie mogą nawiązać z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Plik cookie*  
 Wskaźnik do wartość, która identyfikuje obiekt klasy, którego rejestracja ma zostać odwołane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)