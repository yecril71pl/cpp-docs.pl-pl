---
title: is_trivially_default_constructible — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 19a5e8afedf3e59d5dafa937af4f7d35343eb7d9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459652"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible — klasa

Testuje, czy typ ma prosty Konstruktor domyślny.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma prosty Konstruktor, w przeciwnym razie ma wartość false.

Domyślny konstruktor dla klasy *ty* jest prosty, jeśli:

- jest to niejawnie zadeklarowany Konstruktor domyślny

- Klasa *ty* nie ma żadnych funkcji wirtualnych

- Klasa *ty* nie ma wirtualnych baz.

- wszystkie bezpośrednie bazy klasy *ty* mają uproszczone konstruktory

- klasy wszystkich niestatycznych składowych danych typu klasy mają proste konstruktory

- klasy wszystkich niestatycznych składowych danych typu Array klasy mają proste konstruktory

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
