---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: cf4cea35386d1f781d6d2946c1730ba2e18dacea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624047"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft Specific**

Wywołania **wersji** funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.

## <a name="syntax"></a>Składnia

```
void Release( );
```

## <a name="remarks"></a>Uwagi

Wywołania `IUnknown::Release` wskaźnika zhermetyzowany interfejs wywoływanie `E_POINTER` błąd, jeśli ten wskaźnik interfejsu ma wartość NULL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)