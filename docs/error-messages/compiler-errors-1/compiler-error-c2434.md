---
title: Błąd kompilatora C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205468"
---
# <a name="compiler-error-c2434"></a>Błąd kompilatora C2434

> "*symbol*": symbol zadeklarowany z __declspec (Process) nie może być inicjowany dynamicznie w/CLR: Pure Mode

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Nie można dynamicznie zainicjować zmiennej dla procesu w opcji **/CLR: Pure**. Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) i [proces](../../cpp/process.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2434. Aby rozwiązać ten problem, należy użyć stałych do zainicjowania zmiennych `process`.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
