---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450531"
---
# <a name="securescl"></a>_SECURE_SCL

Zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), to makro określa, [](../standard-library/checked-iterators.md) czy są włączone Iteratory sprawdzane. Domyślnie zaznaczone Iteratory są włączane w kompilacjach debugowania i wyłączone w kompilacjach detalicznych.

> [!IMPORTANT]
> Bezpośrednie użycie makra _SECURE_SCL jest przestarzałe. Zamiast tego należy użyć _ITERATOR_DEBUG_LEVEL, aby kontrolować wybrane ustawienia iteratora. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

Gdy wybrane Iteratory są włączone, niebezpieczne użycie iteratora powoduje błąd w czasie wykonywania, a program zostaje przerwany. Aby włączyć sprawdzone Iteratory, ustaw _ITERATOR_DEBUG_LEVEL na 1 lub 2. Jest to równoznaczne z ustawieniem _SECURE_SCL równym 1 lub Enabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Aby wyłączyć sprawdzone Iteratory, ustaw _ITERATOR_DEBUG_LEVEL na 0. Jest to równoznaczne z ustawieniem _SECURE_SCL równym 0 lub wyłączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Aby uzyskać informacje na temat sposobu wyłączania ostrzeżeń dotyczących sprawdzonych iteratorów, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Zobacz także

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Sprawdzone Iteratory](../standard-library/checked-iterators.md)\
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)\
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)
