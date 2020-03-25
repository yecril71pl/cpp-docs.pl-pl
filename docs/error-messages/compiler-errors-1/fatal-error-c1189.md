---
title: Błąd krytyczny C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203650"
---
# <a name="fatal-error-c1189"></a>Błąd krytyczny C1189

> **błąd\#:** *komunikat o błędzie podany przez użytkownika*

## <a name="remarks"></a>Uwagi

C1189 jest generowana przez dyrektywę `#error`. Deweloper, który koduje dyrektywę określa tekst komunikatu o błędzie. Aby uzyskać więcej informacji, zobacz [#error dyrektywie (CC++/)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C1189. W przykładzie deweloper wystawia niestandardowy komunikat o błędzie, ponieważ nie zdefiniowano identyfikatora `_WIN32`:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Zobacz też

[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
