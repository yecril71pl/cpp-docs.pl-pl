---
title: Błąd kompilatora C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: 1872672e776ad13bf16be5ae69729f4f68d8f3b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302036"
---
# <a name="compiler-error-c2357"></a>Błąd kompilatora C2357

'Identyfikator': musi być funkcją typu "type"

Twój kod deklaruje wersję `atexit` funkcja, która nie jest zgodna z wersją zadeklarowana wewnętrznie przez kompilator. Zadeklaruj `atexit` w następujący sposób:

```
int __cdecl atexit(void (__cdecl *)());
```

Aby uzyskać więcej informacji, zobacz [init_seg](../../preprocessor/init-seg.md).

Poniższy przykład spowoduje wygenerowanie C2357:

```
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```