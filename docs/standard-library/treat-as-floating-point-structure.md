---
title: treat_as_floating_point — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685114"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point — Struktura

Określa, czy `Rep` może być traktowany jako typ zmiennoprzecinkowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Uwagi

`Rep` może być traktowany jako typ zmiennoprzecinkowy tylko wtedy, gdy specjalizacja `treat_as_floating_point<Rep>` pochodzi od [true_type](../standard-library/type-traits-typedefs.md#true_type). Szablon klasy może być wyspecjalizowany dla typu zdefiniowanego przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Przestrzeń nazw:** std:: Chrono

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[\<chrono >](../standard-library/chrono.md)
