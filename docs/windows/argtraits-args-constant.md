---
title: ArgTraits::args, stała | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03db2fd8853321e4a9320f2c17b05800b87e466c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652965"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args — Stała
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Uwagi  
 Śledzi liczbę parametrów `Invoke` metodę interfejsu delegata.  
  
## <a name="remarks"></a>Uwagi  
 Gdy **args** równa -1 wskazuje, może wystąpić w przypadku niezgodności `Invoke` podpis metody.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Argtraits — struktura](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)