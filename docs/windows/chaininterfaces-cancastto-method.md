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
ms.openlocfilehash: 8398f0bd4d9fdc786926782b13ebcac913a6a351
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612873"
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