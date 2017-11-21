---
title: "ActivationFactory::GetIids — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs: C++
helpviewer_keywords: GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4fb9d71da187e12f119dd9b020e1bbab730855c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids — Metoda
Pobiera tablica zaimplementowanego interfejsu identyfikatorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iidCount`  
 Po zakończeniu tej operacji, liczba identyfikatorów interace w `iids` tablicy.  
  
 `iids`  
 Po zakończeniu tej operacji, tablicę zaimplementowany interfejs identyfikatorów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisujący błąd. E_OUTOFMEMORY jest możliwy błąd HRESULT.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Activationfactory — klasa](../windows/activationfactory-class.md)