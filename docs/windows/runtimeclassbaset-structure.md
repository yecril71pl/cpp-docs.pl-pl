---
title: "Runtimeclassbaset — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs: C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fd2f654a27792336488d950a72cedfa4b3ed6527
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   unsigned int RuntimeClassTypeT  
>  
friend struct Details::RuntimeClassBaseT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `RuntimeClassTypeT`  
 Pole flagi, które określa jedną lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Udostępnia metody pomocnicze do `QueryInterface` operacje i pobieranie identyfikatorów interfejsu.  
  
## <a name="members"></a>Elementy członkowskie  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RuntimeClassBaseT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (Biblioteka środowiska uruchomieniowego systemu Windows)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)