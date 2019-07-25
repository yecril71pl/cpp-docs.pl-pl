---
title: is_trivially_copy_constructible — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447988"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible — klasa

Testuje, czy typ ma Konstruktor prostego kopiowania.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest klasą, która ma Konstruktor kopiujący, w przeciwnym razie ma wartość false.

Konstruktor kopiujący dla klasy *t* jest uproszczony, jeśli jest niejawnie zadeklarowany, Klasa *t* nie ma żadnych funkcji wirtualnych ani wirtualnych baz danych, wszystkie bezpośrednie bazy klasy *t* mają konstruktory prostej kopii, klasy wszystkich niestatycznych elementów członkowskich Typ klasy ma konstruktory prostej kopii, a klasy wszystkich niestatycznych składowych danych typu Array klasy mają konstruktory prostej kopii.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
