---
title: Błąd krytyczny C1189 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/27/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49f227b5fda20ab0ba202d3d7eca99492509b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fatal-error-c1189"></a>Błąd krytyczny C1189

> **\#Błąd:** *komunikat o błędzie podanych przez użytkownika.*

## <a name="remarks"></a>Uwagi

C1189 jest generowany przez `#error` dyrektywy. Projektanta, który kodów dyrektywa określa tekst komunikatu o błędzie. Aby uzyskać więcej informacji, zobacz [#error — dyrektywa (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C1189. W przykładzie dewelopera wystawia niestandardowy komunikat o błędzie, ponieważ `_WIN32` nie zdefiniowano identyfikatora:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Zobacz także

[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)