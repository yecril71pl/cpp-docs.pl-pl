---
title: VerifyInheritanceHelper::Verify, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04bf01b5fad5a9fec579e347497a28b5e8abb861
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018819"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
static void Verify();  
```  
  
## <a name="remarks"></a>Uwagi  
 Testuje dwa interfejsy, które są określone przez bieżący parametry szablonu i określa, czy jeden interfejs jest tworzony na podstawie innych.  
  
 Błąd jest emitowane, jeśli jeden interfejs nie pochodzi od innych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Verifyinheritancehelper — struktura](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)