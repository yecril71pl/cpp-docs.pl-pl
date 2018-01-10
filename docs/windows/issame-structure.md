---
title: "Issame — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::IsSame
dev_langs: C++
helpviewer_keywords: IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bae4ecb6f03b7b1cdb0fae02f211dd613e7c39d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="issame-structure"></a>IsSame — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T1,  
   typename T2  
>  
struct IsSame;  
template <  
   typename T1  
>  
struct IsSame<T1, T1>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T1`  
 Typ.  
  
 `T2`  
 Innego typu.  
  
## <a name="remarks"></a>Uwagi  
 Testy czy określić jeden typ jest taki sam jak inny określony typ.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IsSame::value, stała](../windows/issame-value-constant.md)|Wskazuje, czy jeden typ jest taki sam jak inny.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IsSame`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)