---
title: "ChainInterfaces::CanCastTo — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99738f9c5335ede5dafe60e35b3104951f5fb556
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 `true`Jeśli wszystkie operacje rzutowania zakończyło się pomyślnie; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Chaininterfaces — struktura](../windows/chaininterfaces-structure.md)