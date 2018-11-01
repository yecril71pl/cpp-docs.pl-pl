---
title: is_copy_assignable, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: 75e0e8d995fbb3c6bfb1af3142a98651d7a29e96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567859"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable, klasa

Testy czy typ ma można kopiować przypisania.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która zawiera operator przypisania kopii, w przeciwnym razie przechowuje wartość false. Odpowiednikiem is_assignable\<Ty & const Ty & >.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
