---
title: Błąd kompilatora C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446244"
---
# <a name="compiler-error-c3862"></a>Błąd kompilatora C3862

> "*funkcja*": nie można kompilować niezarządzanej funkcji z/CLR: pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Kompilacja z **/CLR: pure** lub **/CLR: Safe** generuje obraz tylko MSIL, obraz bez natywnego (niezarządzanego) kodu.  W związku z tym, nie można użyć `unmanaged` pragmy w **/CLR: pure** lub **/CLR: Safe** kompilacji.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```