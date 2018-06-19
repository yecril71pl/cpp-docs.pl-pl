---
title: ChainInterfaces::CanCastTo — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c2286c347fbd68f34fac807e80facca0a0286aa6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860297"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo — Metoda
Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na poszczególnych specjalizacje zdefiniowane przez parametry szablonu z systemem innym niż domyślny.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identyfikatora interfejsu.  
  
 `ppv`  
 Wskaźnik do identyfikator ostatniego interfejsu, który został pomyślnie rzutowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wszystkie operacje rzutowania zakończyło się pomyślnie; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)