---
title: treat_as_floating_point — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 4cf3ac5be972d8636f1d3dbda3b195f4012517be
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459881"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point — Struktura

Określa, `Rep` czy może być traktowany jako typ zmiennoprzecinkowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Uwagi

`Rep`może być traktowany jako typ zmiennoprzecinkowy tylko wtedy, gdy specjalizacja `treat_as_floating_point<Rep>` pochodzi od [true_type](../standard-library/type-traits-typedefs.md#true_type). Klasa szablonu może być wyspecjalizowana dla typu zdefiniowanego przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Chrono >

**Przestrzeń nazw:** std:: Chrono

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
