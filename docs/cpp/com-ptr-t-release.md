---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: 73de3c2d19063f0738b8b0a3c510ea520f58de0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745055"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Specyficzne dla firmy Microsoft**

Wywołuje release funkcji **elementu** członkowskiego `IUnknown` na encapsulated wskaźnik interfejsu.

## <a name="syntax"></a>Składnia

```cpp
void Release( );
```

## <a name="remarks"></a>Uwagi

Wywołuje `IUnknown::Release` zhermetyzowany wskaźnik interfejsu, `E_POINTER` wywołując błąd, jeśli ten wskaźnik interfejsu jest NULL.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t — Klasa](../cpp/com-ptr-t-class.md)
