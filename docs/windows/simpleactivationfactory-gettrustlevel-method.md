---
title: SimpleActivationFactory::GetTrustLevel, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22fa30a3662897b171245da194573ec17da2f64e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645191"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel — Metoda
Pobiera poziom zaufania wystąpienia klasy określonej przez `Base` parametru szablonu klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
### <a name="parameters"></a>Parametry  
 *trustLvl*  
 Gdy ta operacja zostanie ukończone, poziom zaufania bieżącego obiektu klasy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)