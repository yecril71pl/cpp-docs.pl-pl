---
title: Asweak — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0f4645a6008b954833bf282971a0d3912e1d598
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653147"
---
# <a name="asweak-function"></a>AsWeak — Funkcja
Pobiera słabe odwołanie do określonego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Wskaźnik do typu parametru *p*.  
  
 *p*  
 Wystąpienie typu.  
  
 *pWeak*  
 Po zakończeniu tej operacji, wskaźnik do słabe odwołanie do parametru *p*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)