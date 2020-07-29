---
title: Klasa is_literal_type
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: d5b750755f2499c89e91e497ed03244a11484871
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212257"
---
# <a name="is_literal_type-class"></a>Klasa is_literal_type

Testuje, czy typ może być używany jako **`constexpr`** zmienna, czy być skonstruowany, używany przez lub zwrócony z **`constexpr`** funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest *typem literału*, w przeciwnym razie ma wartość false. Typ literału to **`void`** , typ skalarny, typ referencyjny, tablica typu literału lub typ klasy literału. Typ klasy literału jest typem klasy, który ma prosty destruktor, jest typem agregującym lub ma co najmniej jeden Konstruktor, który nie należy do przenoszenia, **`constexpr`** a wszystkie jego klasy bazowe i niestatyczne elementy członkowskie danych są typami literałów nietrwałych. Chociaż typ literału zawsze jest typem literału, pojęcie typu literału zawiera wszystkie elementy, które kompilator może oszacować jako **`constexpr`** w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
