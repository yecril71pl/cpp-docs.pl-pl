---
title: "AsyncBase::GetOnProgress — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs: C++
helpviewer_keywords: GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e61287c0c6022775cab29f5170c7033ee6a7fab0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress — Metoda
Kopiuje adres bieżący postęp obsługi zdarzeń do określonej zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 `progressHandler`  
 Lokalizacja przechowywania adres bieżącej obsługi zdarzeń postępu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)