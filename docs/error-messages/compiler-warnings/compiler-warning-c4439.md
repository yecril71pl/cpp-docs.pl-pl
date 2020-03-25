---
title: Ostrzeżenie kompilatora C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: c125fa84119c62e3090611c9a841f46eee759711
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165213"
---
# <a name="compiler-warning-c4439"></a>Ostrzeżenie kompilatora C4439

"Function": definicja funkcji z typem zarządzanym w podpisie musi mieć __clrcall konwencją wywoływania

Kompilator niejawnie zamienił konwencję wywoływania na [__clrcall](../../cpp/clrcall.md). Aby rozwiązać ten problem, Usuń konwencję wywoływania `__cdecl` lub `__stdcall`.

C4439 jest zawsze wystawiony jako błąd. To ostrzeżenie można wyłączyć za pomocą `#pragma warning` lub **/WD**; Aby uzyskać więcej informacji, zobacz [Ostrzeżenie](../../preprocessor/warning.md) lub [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
