---
title: treat_as_floating_point — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
dev_langs:
- C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96687959ce4fdd7b5431611a64b878cf05f855ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853303"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point — Struktura

Określa, czy `Rep` może być traktowana jako typ zmiennoprzecinkowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Uwagi

`Rep` może być traktowana jako typ zmiennoprzecinkowy tylko wtedy, gdy specjalizacji `treat_as_floating_point<Rep>` jest pochodną [true_type](../standard-library/type-traits-typedefs.md#true_type). Klasy szablonu może być specjalizowany dla typu zdefiniowanego przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
