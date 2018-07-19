---
title: _HAS_ITERATOR_DEBUGGING | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81f0509c6230020b586c0341e1de608981c05476
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965982"
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
