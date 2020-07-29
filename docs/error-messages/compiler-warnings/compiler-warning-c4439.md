---
title: Ostrzeżenie kompilatora C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: baf74733c94fdb03f130d2300d0918845cc4de4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223333"
---
# <a name="compiler-warning-c4439"></a>Ostrzeżenie kompilatora C4439

"Function": definicja funkcji z typem zarządzanym w podpisie musi mieć __clrcall konwencją wywoływania

Kompilator niejawnie zastąpił konwencją wywoływania z [`__clrcall`](../../cpp/clrcall.md) . Aby rozwiązać ten problem, Usuń **`__cdecl`** **`__stdcall`** konwencję wywoływania lub.

C4439 jest zawsze wystawiony jako błąd. Aby uzyskać więcej informacji, można wyłączyć to ostrzeżenie z `#pragma warning` lub **`/wd`** ; Zobacz [Ostrzeżenie](../../preprocessor/warning.md) lub [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
