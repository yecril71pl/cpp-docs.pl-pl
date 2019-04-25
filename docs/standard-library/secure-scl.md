---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: dcfaee2906136dffbe79a49f089a079104112e78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295750"
---
# <a name="securescl"></a>_SECURE_SCL

Zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), definiuje to makro czy [Checked Iterators](../standard-library/checked-iterators.md) są włączone. Domyślnie Iteratory sprawdzane są włączone w kompilacjach do debugowania i wyłączone w sprzedaży detalicznej.

> [!IMPORTANT]
> Bezpośrednie korzystanie z makro _SECURE_SCL jest przestarzały. Zamiast tego należy użyć _ITERATOR_DEBUG_LEVEL ustawienia iteratora kontroli sprawdzane. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

Gdy Iteratory sprawdzane są włączone, niebezpieczne użycie iteratora powoduje błąd w czasie wykonywania, a program jest zamykany. Aby włączyć Iteratory sprawdzane, ustaw _ITERATOR_DEBUG_LEVEL 1 lub 2. Jest odpowiednikiem ustawienia _SECURE_SCL 1 lub włączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Aby wyłączyć Iteratory sprawdzane, należy ustawić _ITERATOR_DEBUG_LEVEL na 0. Jest odpowiednikiem _SECURE_SCL ustawienie wartości 0 lub wyłączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Aby uzyskać informacji na temat sposobu wyłączania ostrzeżeń dotyczących sprawdzonych iteratorów, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Zobacz także

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Zaznaczone iteratory](../standard-library/checked-iterators.md)<br/>
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)<br/>
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
