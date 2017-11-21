---
title: "AsyncBase::PutOnProgress — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs: C++
helpviewer_keywords: PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4486e3d0bcf929445d4f2e98779ea5339512299b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress — Metoda
Ustawia adres programu obsługi zdarzeń postępu na określoną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 `progressHandler`  
 Adres, do którego program obsługi zdarzeń postępu jest ustawiona.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)