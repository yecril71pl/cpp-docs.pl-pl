---
title: "ActivationFactory::Release — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::Release
dev_langs: C++
helpviewer_keywords: Release method
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b28e49a391cc50f31f14d1f09161e0b9a8faefe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactoryrelease-method"></a>ActivationFactory::Release — Metoda
Zmniejsza odwołanie liczba bieżącego obiektu activationfactory —.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ActivationFactory, klasa](../windows/activationfactory-class.md)