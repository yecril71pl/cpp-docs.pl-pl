---
title: Ostrzeżenie kompilatora C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: bbb69cccbf93be6e97d13db5008780f57e63f9da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537569"
---
# <a name="compiler-warning-c4936"></a>Ostrzeżenie kompilatora C4936

> Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

A `__declspec` modyfikator użyto ale `__declspec` modyfikator tylko jest prawidłowa, gdy kompilowany przy użyciu jednego z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcje.

Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).

C4936 zawsze jest wystawiany jako błąd.  Można wyłączyć C4936 z [ostrzeżenie](../../preprocessor/warning.md) pragmy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```