---
title: Dontusenewusemake — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f343d0b47d50cd375d186c29ff55b91898aa9c61
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Uwagi  
 Zapobiega przy użyciu operatora `new` w runtimeclass —. W związku z tym, należy użyć [Make — funkcja](../windows/make-function.md) zamiast tego.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DontUseNewUseMake::operator nowy operator](../windows/dontusenewusemake-operator-new-operator.md)|Overloads operator `new` i uniemożliwia użycie w runtimeclass —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make, funkcja](../windows/make-function.md)