---
title: treat_as_floating_point — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 1b7b58983032ee74ed3d88feb7325cd537e1cc2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493863"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point — Struktura

Określa, czy `Rep` może być traktowana jako typ zmiennoprzecinkowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Uwagi

`Rep` może być traktowana jako typ zmiennoprzecinkowy tylko wtedy, gdy specjalizacja `treat_as_floating_point<Rep>` jest tworzony na podstawie [true_type](../standard-library/type-traits-typedefs.md#true_type). Klasa szablonu może być specjalistyczna dla typu zdefiniowanego przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
