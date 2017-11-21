---
title: "SimpleActivationFactory::GetTrustLevel — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs: C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb709d0f79a1fd57dfe84567b0bc7f8d1d15c3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel — Metoda
Pobiera poziom zaufania wystąpienia z klasą określoną przez `Base` parametr szablonu klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### <a name="parameters"></a>Parametry  
 `trustLvl`  
 Po tej operacji zakończeniu poziom zaufania bieżącego obiektu klasy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Simpleactivationfactory — klasa](../windows/simpleactivationfactory-class.md)