---
title: Isbaseofstrict — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9066a9cd8985b132c1fbd9f6a97bcd0654003d2
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604506"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowy*  
 Typ podstawowy.  
  
 *Pochodne*  
 Typ pochodny.  
  
## <a name="remarks"></a>Uwagi  
 Sprawdza, czy jest jeden typ podstawowy innego.  
  
 Pierwszy szablon sprawdza, czy typ pochodzi od typu podstawowego, który może prowadzić **true** lub **false**. Drugi sprawdza, czy typ jest pochodną, która zawsze daje w wyniku **false**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constants"></a>Publiczne stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IsBaseOfStrict::value, stała](../windows/isbaseofstrict-value-constant.md)|Wskazuje, czy jeden typ jest podstawą innego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)