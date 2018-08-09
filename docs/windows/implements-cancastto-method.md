---
title: Implements::CanCastTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a73aac6fb36270f0cd04615d9e530b29841850f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010925"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo — Metoda
Pobiera wskaźnik do określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu.  
  
 *ppv*  
 Jeśli operacja się powiedzie, wskaźnik do interfejsu określonego przez *riid*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie HRESULT, która wskazuje błąd, takich jak E_NOINTERFACE.  
  
## <a name="remarks"></a>Uwagi  
 Jest to funkcja pomocnicza wewnętrznej, która wykonuje operację QueryInterface.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Implements, struktura](../windows/implements-structure.md)