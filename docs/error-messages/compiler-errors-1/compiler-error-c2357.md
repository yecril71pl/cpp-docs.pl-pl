---
title: Błąd kompilatora C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759922"
---
# <a name="compiler-error-c2357"></a>Błąd kompilatora C2357

"Identyfikator": musi być funkcją typu "Type"

Kod deklaruje wersję funkcji `atexit`, która nie jest zgodna z wersją zadeklarowaną wewnętrznie przez kompilator. Zadeklaruj `atexit` w następujący sposób:

```
int __cdecl atexit(void (__cdecl *)());
```

Aby uzyskać więcej informacji, zobacz [init_seg](../../preprocessor/init-seg.md).

Poniższy przykład generuje C2357:

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
