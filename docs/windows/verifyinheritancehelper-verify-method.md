---
title: "VerifyInheritanceHelper::Verify — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs: C++
helpviewer_keywords: Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffc08fd7cd59d463d5a53ababf3acb6baef9e3ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
static void Verify();  
```  
  
## <a name="remarks"></a>Uwagi  
 Testy dwa interfejsy określoną przez parametry bieżącego szablonu i określa, czy jeden interfejs pochodzi od innych.  
  
 Błąd jest emitowany, jeśli jeden interfejs nie pochodzi od innych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Verifyinheritancehelper — struktura](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)