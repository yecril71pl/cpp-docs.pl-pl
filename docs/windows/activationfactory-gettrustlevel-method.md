---
title: ActivationFactory::GetTrustLevel, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bddc5a453e1c3aac43fe58d105ccef863c67808
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652272"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel — Metoda
Pobiera poziom zaufania, obiektu, który bieżącego **activationfactory —** tworzy wystąpienie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
### <a name="parameters"></a>Parametry  
 *trustLvl*  
 Po zakończeniu tej operacji, poziom zaufania środowiska uruchomieniowego klasy **activationfactory —** tworzy wystąpienie.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie jest emitowane Błąd asercji i *trustLvl* ustawiono `FullTrust`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ActivationFactory, klasa](../windows/activationfactory-class.md)