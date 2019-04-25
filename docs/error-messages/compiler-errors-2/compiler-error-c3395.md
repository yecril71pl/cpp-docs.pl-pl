---
title: Błąd kompilatora C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: 2e5234abcbe46e17035fd0b16e9816c879d86cfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243053"
---
# <a name="compiler-error-c3395"></a>Błąd kompilatora C3395

'Funkcja': nie można zastosować atrybutu __declspec(dllexport) do funkcji z \__clrcall konwencji wywoływania

`__declspec(dllexport)` i [__clrcall](../../cpp/clrcall.md) nie są zgodne.  Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).

Poniższy przykład spowoduje wygenerowanie C3395:

```
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```