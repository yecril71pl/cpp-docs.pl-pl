---
title: ChainInterfaces::CanCastTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ff24ac92e5e84cb85127ef6e33805928fabd6f60
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647534"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo — Metoda
Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na każdej specjalizacji zdefiniowane przez parametry szablonu innych niż domyślne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Identyfikator interfejsu.  
  
 *ppv*  
 Wskaźnik do ostatniego Identyfikatora interfejsu, który został pomyślnie rzutowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wszystkie operacje rzutowania zakończyło się pomyślnie; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)