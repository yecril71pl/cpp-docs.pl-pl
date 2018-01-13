---
title: "InvokeHelper::Invoke — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs: C++
helpviewer_keywords: Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8707ac96c0417eddb015d7e802433bf071dda80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
#### <a name="parameters"></a>Parametry  
 `arg1`  
 Argument 1.  
  
 `arg2`  
 Argument 2.  
  
 `arg3`  
 Argument 3.  
  
 `arg4`  
 Argument 4.  
  
 `arg5`  
 Argument 5.  
  
 `arg6`  
 Argument 6.  
  
 `arg7`  
 Argument 7.  
  
 `arg8`  
 Argument 8.  
  
 `arg9`  
 Argument 9.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisującego błąd.  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje program obsługi zdarzeń, którego sygnatura zawiera określoną liczbę argumentów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Invokehelper — struktura](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)