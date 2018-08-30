---
title: Kompilator ostrzeżenie (poziom 1) C4612 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10a0a5640386f5e5673f39d6c2c76ee18fcc7ba7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210733"
---
# <a name="compiler-warning-level-1-c4612"></a>Kompilator ostrzeżenie (poziom 1) C4612

> Błąd w nazwie pliku dołączanego

## <a name="remarks"></a>Uwagi

Ostrzeżenie to pojawia się za pomocą **#pragma include_alias** gdy nazwa pliku jest nieprawidłowe lub niekompletne.

Argumenty **#pragma include_alias** instrukcji można użyć formy oferty ("*filename*") lub formularz nawias kątowy (\<*filename*>), ale oba muszą Użyj tego samego formularza.

## <a name="example"></a>Przykład

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```