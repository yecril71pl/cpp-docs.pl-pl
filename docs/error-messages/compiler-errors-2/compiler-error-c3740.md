---
title: Błąd kompilatora C3740
ms.date: 11/04/2016
f1_keywords:
- C3740
helpviewer_keywords:
- C3740
ms.assetid: edb17a90-2307-4df6-943d-580460d26d2b
ms.openlocfilehash: 4e32c37853f4c877e6260e38daa0c8357ca54a25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752668"
---
# <a name="compiler-error-c3740"></a>Błąd kompilatora C3740

szablony nie mogą być źródłem ani odbierać zdarzeń

Klasa lub struktura z szablonem nie może zawierać [zdarzeń](../../cpp/event-handling.md).

Poniższy przykład generuje C3740:

```cpp
// C3740.cpp
template <typename T>   // Delete the template specification
struct E {
   __event void f();   // C3740
};

int main() {
}
```
