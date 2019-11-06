---
title: Ostrzeżenie kompilatora C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623655"
---
# <a name="compiler-warning-c4439"></a>Ostrzeżenie kompilatora C4439

"Function": definicja funkcji z typem zarządzanym w podpisie musi mieć konwencję wywoływania __clrcall

Kompilator niejawnie zastąpił konwencją wywoływania z [__clrcall](../../cpp/clrcall.md). Aby rozwiązać ten problem, Usuń konwencję wywoływania `__cdecl` lub `__stdcall`.

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