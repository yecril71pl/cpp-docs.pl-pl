---
title: make_signed — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c3c35e28dec3270299329c0186273e324effc2bb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453684"
---
# <a name="makesigned-class"></a>make_signed — Klasa

Ustawia typ lub najmniejszy typ podpisany o wartości większej lub równej rozmiarowi do typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie modyfikatora typu zawiera zmodyfikowany typ, `is_signed<T>` *który ma wartość* true. W przeciwnym razie jest to najmniejszy typ `UT` bez znaku `sizeof (T) <= sizeof (UT)`, dla którego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
