---
title: Błąd kompilatora C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: a36655b0b3a28536538998656d7ce354c409d07c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225530"
---
# <a name="compiler-error-c2381"></a>Błąd kompilatora C2381

"Function": zmiana definicji; __declspec (noreturn) różni się

Funkcja została zadeklarowana, a następnie zdefiniowana, ale definicja użyła modyfikatora [noreturn](../../cpp/noreturn.md) **`__declspec`** . Użycie `noreturn` stanowi ponowną definicję funkcji; deklaracja i definicja muszą wyrazić zgodę na użycie `noreturn` .

Poniższy przykład generuje C2381:

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
