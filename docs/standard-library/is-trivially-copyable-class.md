---
title: is_trivially_copyable, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: 181152bff1d7c2e4f97678b48310f744080822ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554382"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable, klasa

Sprawdza, czy określony typ jest typem kopiowania.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest trywialne typu, w przeciwnym razie przechowuje wartość false. Typy trywialne mieć nie operacji kopiowania nietrywialnymi operacji przenoszenia i destruktory. Ogólnie rzecz biorąc operacja kopiowania jest uważane za trywialne, jeśli można zaimplementować jako kopię bitową. Typy wbudowane i tablic typów trywialne są kopiowania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
