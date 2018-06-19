---
title: Błąd krytyczny C1189 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199797"
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