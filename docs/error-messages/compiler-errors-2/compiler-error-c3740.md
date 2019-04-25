---
title: Błąd kompilatora C3740
ms.date: 11/04/2016
f1_keywords:
- C3740
helpviewer_keywords:
- C3740
ms.assetid: edb17a90-2307-4df6-943d-580460d26d2b
ms.openlocfilehash: dd493e4759b2fb70918bf94f14f4ada022e326b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227004"
---
# <a name="compiler-error-c3740"></a>Błąd kompilatora C3740

Szablony nie źródła lub odbieranie zdarzeń

Szablonem klasy lub struktury nie mogą zawierać [zdarzenia](../../cpp/event-handling.md).

Poniższy przykład spowoduje wygenerowanie C3740:

```
// C3740.cpp
template <typename T>   // Delete the template specification
struct E {
   __event void f();   // C3740
};

int main() {
}
```