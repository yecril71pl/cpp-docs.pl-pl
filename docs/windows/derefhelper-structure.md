---
title: Derefhelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
dev_langs:
- C++
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e5c4965ab8a013fdd52e6dfa51e74bfbf54ed73
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651538"
---
# <a name="derefhelper-structure"></a>DerefHelper — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
   typename T  
>  
struct DerefHelper;  
  
template <  
   typename T  
>  
struct DerefHelper<T*>;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Parametr szablonu.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje wskaźnik wyłuskiwany `T*` parametru szablonu.  
  
 **Derefhelper —** jest używana w wyrażeniu, takich jak: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`DerefType`|Identyfikator parametru szablonu wyłuskiwany `T*`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `DerefHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)