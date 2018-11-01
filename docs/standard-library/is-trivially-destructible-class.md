---
title: is_trivially_destructible, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 61d626c308338595a64031a45908ab299ae1a957
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656069"
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible, klasa

Sprawdza, czy typ jest przypadku zniszczalnych.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest typem zniszczalnych i destruktor jest znany w kompilatorze korzystania z nie nietrywialnymi operacji. W przeciwnym razie przechowuje wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
