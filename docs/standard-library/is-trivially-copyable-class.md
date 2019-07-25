---
title: Klasa is_trivially_copyable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: d3062ae311b63be76ba07185f4f8173afa4229cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459741"
---
# <a name="istriviallycopyable-class"></a>Klasa is_trivially_copyable

Testuje, czy typ jest typu, który jest jednocześnie kopiowany.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest typu, który jest jednocześnie kopiowany, w przeciwnym razie ma wartość false. Typy, które można kopiować, nie mają nieuproszczonych operacji kopiowania, operacji przenoszenia lub destruktorów. Ogólnie rzecz biorąc, operacja kopiowania jest traktowana jako uproszczona, jeśli może być zaimplementowana jako kopia bitowa. Zarówno typy wbudowane, jak i tablice typów, które mogą być kopiujące, są proste do skopiowania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
