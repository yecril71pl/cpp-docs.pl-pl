---
title: IsBaseOfStrict — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371350"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Typ podstawowy.

*Pochodne*<br/>
Typ pochodny.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jeden typ jest podstawą innego.

Pierwszy szablon sprawdza, czy typ jest pochodną typu podstawowego, który może przynieść **wartość true** lub **false**. Drugi szablon sprawdza, czy typ jest pochodną samego siebie, co zawsze daje **false**.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Stałe publiczne

Nazwa                            | Opis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::wartość](#value) | Wskazuje, czy jeden typ jest podstawą innego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsBaseOfStrict`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict::wartość

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest podstawą innego.

`value`**true,** jeśli `Base` typ jest klasą `Derived`podstawową typu, w przeciwnym razie jest **false**.
