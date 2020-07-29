---
title: Błąd kompilatora C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: a40a79c48b0f437271063e555593464f55fe9837
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212595"
---
# <a name="compiler-error-c3168"></a>Błąd kompilatora C3168

"Type": niedozwolony typ podstawowy dla wyliczenia

Typ podstawowy określony dla **`enum`** typu jest nieprawidłowy. Typ podstawowy musi być integralnym typem C++ lub odpowiednim typem CLR.

Poniższy przykład generuje C3168:

```cpp
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
