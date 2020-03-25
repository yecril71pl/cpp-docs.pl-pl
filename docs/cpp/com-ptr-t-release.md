---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170595"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję składowej **wydania** elementu `IUnknown` na wyhermetyzowanym wskaźniku interfejsu.

## <a name="syntax"></a>Składnia

```
void Release( );
```

## <a name="remarks"></a>Uwagi

Wywołuje `IUnknown::Release` na hermetyzowanym wskaźniku interfejsu, wywołując błąd `E_POINTER`, jeśli ten wskaźnik interfejsu ma wartość NULL.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
