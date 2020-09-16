---
title: Ostrzeżenie kompilatora (poziom 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 1a9fef0a825f98ab3ce8d935c98eefe1866be6cf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684693"
---
# <a name="compiler-warning-level-1-c4091"></a>Ostrzeżenie kompilatora (poziom 1) C4091

"słowo kluczowe": zignorowane po lewej "Type", gdy nie jest zadeklarowana żadna zmienna

Kompilator wykrył sytuację, w której użytkownik prawdopodobnie zażądał zadeklarowanej zmiennej, ale kompilator nie mógł zadeklarować zmiennej.

## <a name="examples"></a>Przykłady

**`__declspec`** Atrybut na początku deklaracji typu zdefiniowanego przez użytkownika ma zastosowanie do zmiennej tego typu. C4091 wskazuje, że żadna zmienna nie jest zadeklarowana. Poniższy przykład generuje C4091.

```cpp
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

Jeśli identyfikator jest typedef, nie może być również nazwą zmiennej. Poniższy przykład generuje C4091.

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```
