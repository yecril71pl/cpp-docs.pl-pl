---
title: is_trivially_default_constructible — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: b35458ca280285eb699c9b12b15b705660299ef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563673"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible — klasa

Sprawdza, czy typ ma konstruktora domyślnego prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma proste konstruktora, w przeciwnym razie przechowuje wartość false.

Domyślny konstruktor dla klasy *Ty* jest proste jeśli:

- jest niejawnie zadeklarowany Konstruktor domyślny

- Klasa *Ty* ma żadnych funkcji wirtualnych

- Klasa *Ty* ma nie baz wirtualnych

- wszystkie bezpośrednio baz klasy *Ty* mieć konstruktorów prosta

- klasy wszystkie składowe danych niestatycznych typu klasy mieć konstruktorów prosta

- klasy wszystkie składowe danych niestatycznych typu tablicowego klasy mieć konstruktorów prosta

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
