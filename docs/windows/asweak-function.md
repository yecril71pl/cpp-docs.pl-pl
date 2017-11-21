---
title: "Asweak — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::AsWeak
dev_langs: C++
helpviewer_keywords: AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 36cf91b969ac1c180f7060c2518e626a22a08284
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asweak-function"></a>AsWeak — Funkcja
Pobiera słabe odwołanie do określonego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename T  
>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Wskaźnik do typu parametru `p`.  
  
 `p`  
 Wystąpienie typu.  
  
 `pWeak`  
 Po zakończeniu tej operacji, wskaźnik do słabe odwołanie do parametru `p`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli operacja zakończy się pomyślnie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)