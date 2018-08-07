---
title: RuntimeClassBaseT, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec10faf9733bbff3fb271b5465ee70a338c37898
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604996"
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
  
### <a name="parameters"></a>Parametry  
 *RuntimeClassTypeT*  
 Pola flagi, które określa co najmniej jeden [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) modułów wyliczających.  
  
## <a name="remarks"></a>Uwagi  
 Zapewnia metody pomocnika do `QueryInterface` operacji oraz pobieranie identyfikatorów interfejsu.  
  
## <a name="members"></a>Elementy członkowskie  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RuntimeClassBaseT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (Biblioteka środowiska uruchomieniowego Windows)](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)