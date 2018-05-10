---
title: Iid_ppv_args_helper — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper — Funkcja
Sprawdza, czy typ określony argument jest pochodną `IUnknown` interfejsu.  
  
> [!IMPORTANT]
>  Ta specjalizacja szablonu obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie. Użyj [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ argumentu `pp`.  
  
 `pp`  
 Podwójnie pośredni wskaźnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Argument `pp` rzutowania na wskaźnik do a-wskaźnik do `void`.  
  
## <a name="remarks"></a>Uwagi  
 Błąd w czasie kompilacji jest generowany, gdy parametr szablonu `T` nie pochodzi od `IUnknown`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (Biblioteka środowiska uruchomieniowego systemu Windows)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)