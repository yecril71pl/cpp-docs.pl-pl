---
title: ActivationFactory::GetRuntimeClassName, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: edc4658ebf0519ef9d1792d62b303f423e658835
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643072"
---
# <a name="activationfactorygetruntimeclassname-method"></a>ActivationFactory::GetRuntimeClassName — Metoda
Pobiera nazwę klasy środowiska uruchomieniowego, obiektu, który bieżącego **activationfactory —** tworzy wystąpienie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
### <a name="parameters"></a>Parametry  
 *runtimeName*  
 Po zakończeniu tej operacji, dojścia do ciągu, który zawiera nazwę klasy środowiska uruchomieniowego obiektu, bieżący **activationfactory —** tworzy wystąpienie.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ActivationFactory, klasa](../windows/activationfactory-class.md)