---
title: "Dontusenewusemake — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs: C++
helpviewer_keywords: DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 62f8abc151758ac9253698390cbab3e2ba62a4c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[DontUseNewUseMake::operator nowy Operator](../windows/dontusenewusemake-operator-new-operator.md)|Overloads operator `new` i uniemożliwia użycie w runtimeclass —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make — funkcja](../windows/make-function.md)