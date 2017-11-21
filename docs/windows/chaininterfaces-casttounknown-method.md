---
title: "ChainInterfaces::CastToUnknown — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
dev_langs: C++
helpviewer_keywords: CastToUnknown method
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8851396cf817ec52d072ba0bfb6267ec094a82b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfacescasttounknown-method"></a>ChainInterfaces::CastToUnknown — Metoda
Rzutuje wskaźnik interfejsu z typem zdefiniowanym przez `I0` parametr szablonu na wskaźnik do elementu IUnknown.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu IUnknown.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Chaininterfaces — struktura](../windows/chaininterfaces-structure.md)