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
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787323"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*Base*<br/>
Typ podstawowy.

*Pochodne*<br/>
Typ pochodny.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jest jeden typ podstawowy innego.

Pierwszy szablon sprawdza, czy typ pochodzi od typu podstawowego, który może prowadzić **true** lub **false**. Drugi sprawdza, czy typ jest pochodną, która zawsze daje w wyniku **false**.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Publiczne stałe

Nazwa                            | Opis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Wskazuje, czy jeden typ jest podstawą innego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsBaseOfStrict`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest podstawą innego.

`value` jest **true** Jeśli typ `Base` jest klasą bazową typu `Derived`, w przeciwnym razie jest **false**.
