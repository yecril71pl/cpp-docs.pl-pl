---
title: Klasa is_literal_type
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456210"
---
# <a name="isliteraltype-class"></a>Klasa is_literal_type

Testuje, czy typ może być używany jako `constexpr` zmienna, czy być skonstruowany, używany przez lub zwrócony `constexpr` z funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest *typem literału*, w przeciwnym razie ma wartość false. Typ literału to **void**, typ skalarny, typ referencyjny, tablica typu literału lub typ klasy literału. Typ klasy literału jest typem klasy, który ma prosty destruktor, jest typem agregującym lub ma co najmniej jeden `constexpr` Konstruktor, który nie należy do przenoszenia, a wszystkie jego klasy bazowe i niestatyczne elementy członkowskie danych są typami literałów nietrwałych. Chociaż typ literału zawsze jest typem literału, pojęcie typu literału zawiera wszystkie elementy, które kompilator może oszacować jako `constexpr` w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
