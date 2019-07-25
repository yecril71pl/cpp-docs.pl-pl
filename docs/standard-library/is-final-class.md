---
title: Klasa is_final
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: 14efbeb33193cc674c6e766b880e89d9b76d140a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452654"
---
# <a name="isfinal-class"></a>Klasa is_final

Testuje, czy typ jest oznaczony `final`typem klasy.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest oznaczony jako `final`typ klasy, w przeciwnym razie ma wartość false. Jeśli *T* jest typem klasy, musi być kompletnym typem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[final, specyfikator](../cpp/final-specifier.md)
