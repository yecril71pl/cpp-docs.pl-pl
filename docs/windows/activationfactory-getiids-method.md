---
title: ActivationFactory::GetIids, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aaaa8d5bb0a88b9078c60fa61608e52fafd5baac
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643514"
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids — Metoda
Pobiera tablicę zaimplementowanego interfejsu identyfikatorów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Parametry  
 *iidCount*  
 Po zakończeniu tej operacji, liczba identyfikatorów interfejsu w *IID* tablicy.  
  
 *IID*  
 Po zakończeniu tej operacji, tablicę implementowane identyfikatorów interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. E_OUTOFMEMORY jest możliwe błąd HRESULT.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ActivationFactory, klasa](../windows/activationfactory-class.md)