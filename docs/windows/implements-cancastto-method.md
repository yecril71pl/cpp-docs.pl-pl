---
title: "Implements::CanCastTo — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 83d217cb749c350da45bcae2159e6b46d03f68cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo — Metoda
Pobiera wskaźnik do określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odwołanie do identyfikatora interfejsu.  
  
 `ppv`  
 Jeśli powodzenia wskaźnik do interfejsu określony przez `riid`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który wskazuje błąd, takich jak E_NOINTERFACE.  
  
## <a name="remarks"></a>Uwagi  
 Jest to wewnętrzny pomocnika funkcji, która wykonuje operację QueryInterface.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — struktura](../windows/implements-structure.md)