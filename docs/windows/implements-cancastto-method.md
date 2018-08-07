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
ms.openlocfilehash: 53b17558998812895ece4b47f5de03700e502b8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608946"
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