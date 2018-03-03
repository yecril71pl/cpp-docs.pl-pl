---
title: "Implementshelper — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a51de59278e476be1e99b60ef1b0ab8a6e3f3cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementshelper-structure"></a>ImplementsHelper — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>Parametry  
 `RuntimeClassFlagsT`  
 Pole flagi, które określa jedną lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wyliczenia.  
  
 `ILst`  
 Lista identyfikatorów interfejsu.  
  
 `IsDelegateToClass`  
 Określ `true` Jeśli bieżące wystąpienie klasy implementuje jest klasą podstawową pierwszy identyfikatora interfejsu w `ILst`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Ułatwia wdrożenie [implementuje](../windows/implements-structure.md) struktury.  
  
 Ten szablon przechodzi przez listę interfejsów i dodaje je jako klasy podstawowe, jak i informacje niezbędne do włączenia QueryInterface.  
  
## <a name="members"></a>Elementy członkowskie  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (Biblioteka środowiska uruchomieniowego systemu Windows)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)