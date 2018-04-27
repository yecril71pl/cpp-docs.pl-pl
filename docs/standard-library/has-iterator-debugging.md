---
title: _HAS_ITERATOR_DEBUGGING | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e6cf83c0877c351a2bf247a557f3df53e9c1f22
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Zastąpiony przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), to makro definiuje, czy iteratora funkcję debugowania jest włączony w kompilacji debugowania. Domyślnie debugowania iteratora jest włączona w kompilacjach debugowania i wyłączone w sprzedaży detalicznej kompilacji. Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Bezpośrednie użycie `_HAS_ITERATOR_DEBUGGING` makro jest przestarzały. Zamiast tego należy użyć `_ITERATOR_DEBUG_LEVEL` kontrolować ustawienia debugowania iteratora. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

Aby włączyć debugowanie w kompilacjach debugowania iteratora, ustaw `_ITERATOR_DEBUG_LEVEL` 2. Jest to równoważne `_HAS_ITERATOR_DEBUGGING` ustawienie 1 lub włączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

`_ITERATOR_DEBUG_LEVEL` Nie można ustawić 2 (i `_HAS_ITERATOR_DEBUGGING` nie może być ustawiona na 1) w sprzedaży detalicznej kompilacji.

Aby wyłączyć Iteratory debugowania w kompilacjach debugowania, ustaw `_ITERATOR_DEBUG_LEVEL` 0 lub 1. Jest to równoważne `_HAS_ITERATOR_DEBUGGING` ustawienie 0 lub wyłączone:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Zobacz także

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)<br/>
[Zaznaczone iteratory](../standard-library/checked-iterators.md)<br/>
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
