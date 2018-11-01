---
title: Błąd kompilatora C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587593"
---
# <a name="compiler-error-c2434"></a>Błąd kompilatora C2434

> "*symbol*': zadeklarowanego symbolu z __declspec(process) nie można zainicjować dynamicznie w/CLR: pure tryb czysty

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Nie jest możliwe dynamicznie zainicjować zmienną na proces w ramach **/CLR: pure**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [procesu](../../cpp/process.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2434. Aby rozwiązać ten problem, użyj stałych, aby zainicjować `process` zmiennych.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```