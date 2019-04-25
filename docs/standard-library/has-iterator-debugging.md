---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: 339c32f9b487db2e318f8763ac01a0d155fc1dc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159707"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), definiuje to makro, czy debugowania funkcji iteratora jest włączony w kompilacji debugowania. Domyślnie debugowania iteratora jest włączona w kompilacjach do debugowania i wyłączone w sprzedaży detalicznej. Aby uzyskać więcej informacji, zobacz [Debug Iterator Support](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Bezpośrednie korzystanie z makro _HAS_ITERATOR_DEBUGGING jest przestarzały. Zamiast tego należy użyć _ITERATOR_DEBUG_LEVEL, aby kontrolować ustawienia debugowania iteratora. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

Aby włączyć iteratora debugowania w kompilacjach debugowania, ustaw _ITERATOR_DEBUG_LEVEL 2. Jest równoważne ustawieniu _HAS_ITERATOR_DEBUGGING, 1 lub włączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

Nie można ustawić _ITERATOR_DEBUG_LEVEL 2 (i _HAS_ITERATOR_DEBUGGING nie może być ustawiona na 1) w przypadku handlu detalicznego kompilacji.

Aby wyłączyć Iteratory debugowania w kompilacjach debugowania, ustaw _ITERATOR_DEBUG_LEVEL 0 lub 1. Jest odpowiednikiem _HAS_ITERATOR_DEBUGGING ustawienie wartości 0 lub wyłączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Zobacz także

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)<br/>
[Zaznaczone iteratory](../standard-library/checked-iterators.md)<br/>
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
