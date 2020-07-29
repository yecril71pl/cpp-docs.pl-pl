---
title: Błąd kompilatora C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 78be424040c7315271d0880c6678584f698b5be8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218185"
---
# <a name="compiler-error-c2732"></a>Błąd kompilatora C2732

Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla elementu "Function"

Funkcja jest już zadeklarowana z innym specyfikatorem powiązania.

Przyczyną tego błędu może być dołączenie plików z różnymi specyfikatorami powiązania.

Aby naprawić ten błąd, należy zmienić **`extern`** instrukcje w taki sposób, aby powiązania były zgodne. W szczególności nie należy zawijać `#include` dyrektyw w `extern "C"` blokach.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2732:

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
