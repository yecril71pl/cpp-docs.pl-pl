---
title: "Verifyinheritancehelper — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs: C++
helpviewer_keywords: VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 926ed226b67ae510647d2523e4992f6ee3c79a5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I`  
 Typ.  
  
 `Base`  
 Innego typu.  
  
## <a name="remarks"></a>Uwagi  
 Sprawdza, czy jeden interfejs pochodzi z innego interfejsu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify — metoda](../windows/verifyinheritancehelper-verify-method.md)|Testy dwa interfejsy określoną przez parametry bieżącego szablonu i określa, czy jeden interfejs pochodzi od innych.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)