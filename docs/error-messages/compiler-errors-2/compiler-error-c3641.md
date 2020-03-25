---
title: Błąd kompilatora C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 44356fb1a1818a02102d23e6b308457f2f39506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200515"
---
# <a name="compiler-error-c3641"></a>Błąd kompilatora C3641

> "*Function*": nieprawidłowa Konwencja wywoływania "calling_convention" dla funkcji skompilowanej z/CLR: Pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Tylko Konwencja wywoływania [__clrcall](../../cpp/clrcall.md) jest dozwolona z [/CLR: Pure](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3641:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
