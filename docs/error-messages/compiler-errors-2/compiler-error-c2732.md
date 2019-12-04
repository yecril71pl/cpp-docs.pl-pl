---
title: Błąd kompilatora C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755801"
---
# <a name="compiler-error-c2732"></a>Błąd kompilatora C2732

Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla elementu "Function"

Funkcja jest już zadeklarowana z innym specyfikatorem powiązania.

Przyczyną tego błędu może być dołączenie plików z różnymi specyfikatorami powiązania.

Aby naprawić ten błąd, Zmień instrukcje `extern` tak, aby powiązania były zgodne. W szczególności nie należy zawijać `#include` dyrektyw w blokach `extern "C"`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2732:

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
