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
ms.openlocfilehash: 328691877a3b129c852460f8f68cdd3db4974e6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595302"
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