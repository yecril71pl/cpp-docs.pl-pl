---
title: Ostrzeżenie kompilatora (poziom 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185987"
---
# <a name="compiler-warning-level-1-c4612"></a>Ostrzeżenie kompilatora (poziom 1) C4612

> błąd w nazwie pliku dołączanego

## <a name="remarks"></a>Uwagi

To ostrzeżenie występuje **#pragma include_alias** , gdy nazwa pliku jest nieprawidłowa lub nie została podana.

Argumenty do instrukcji **#pragma include_alias** mogą używać formularza cudzysłowu ("*filename*") lub nawiasu klamrowego (\<*filename*>), ale oba muszą używać tego samego formularza.

## <a name="example"></a>Przykład

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
