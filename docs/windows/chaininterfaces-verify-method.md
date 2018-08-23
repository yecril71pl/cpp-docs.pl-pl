---
title: ChainInterfaces::Verify, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6dbc595714cbecf2ad13db13051866e31e5ebcd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581061"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify — Metoda

Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *I9* dziedziczy `IUnknown` i/lub `IInspectable`oraz że *I0* dziedziczy z *I1* za pośrednictwem *I9*.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

## <a name="remarks"></a>Uwagi

W przypadku niepowodzenia operacji weryfikacji **static_assert** emituje komunikat o błędzie opisujący błąd.

Parametry szablonu *I0* i *I1* są wymagane i parametry *I2* za pośrednictwem *I9* są opcjonalne.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)