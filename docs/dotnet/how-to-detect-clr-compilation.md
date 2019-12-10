---
title: 'Instrukcje: Wykrywanie kompilacji CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 42b2952e3b63023ca26c6b1f7d0ccb8871082499
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988215"
---
# <a name="how-to-detect-clr-compilation"></a>Porady: wykrywanie kompilacji /clr

Użyj makra `_MANAGED` lub `_M_CEE`, aby sprawdzić, czy moduł został skompilowany z **/CLR**. Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

Aby uzyskać więcej informacji na temat makr, zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md).

## <a name="example"></a>Przykład

```cpp
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
