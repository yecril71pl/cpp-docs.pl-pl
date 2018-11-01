---
title: Błąd krytyczny C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 06d42316a0109ac063bba43cefebd9aab71c2e72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565532"
---
# <a name="fatal-error-c1189"></a>Błąd krytyczny C1189

> **\#Błąd:** *komunikat o błędzie podanych przez użytkownika.*

## <a name="remarks"></a>Uwagi

C1189 jest generowany przez `#error` dyrektywy. Deweloper, który kodów dyrektywa określa tekst komunikatu o błędzie. Aby uzyskać więcej informacji, zobacz [#error — dyrektywa (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C1189. W tym przykładzie Deweloper generuje niestandardowy komunikat o błędzie, ponieważ `_WIN32` nie zdefiniowano identyfikatora:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Zobacz także

[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)