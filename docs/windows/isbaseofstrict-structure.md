---
title: Isbaseofstrict — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 137f572f01d4aa72b9141c3ca172426fdb575b48
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169527"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*podstawowy*<br/>
Typ podstawowy.

*Pochodne*<br/>
Typ pochodny.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jest jeden typ podstawowy innego.

Pierwszy szablon sprawdza, czy typ pochodzi od typu podstawowego, który może prowadzić `true` lub `false`. Drugi sprawdza, czy typ jest pochodną, która zawsze daje w wyniku `false`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Publiczne stałe

Nazwa                            | Opis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Wskazuje, czy jeden typ jest podstawą innego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsBaseOfStrict`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="value"></a>IsBaseOfStrict::value

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest podstawą innego.

`value` jest `true` Jeśli typ `Base` jest klasą bazową typu `Derived`, w przeciwnym razie jest `false`.
