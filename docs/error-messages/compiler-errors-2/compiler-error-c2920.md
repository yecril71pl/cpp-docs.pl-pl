---
title: Błąd kompilatora C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 28bbbd30bcb16e2ea5fc14fe0f48f86814ee13c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311673"
---
# <a name="compiler-error-c2920"></a>Błąd kompilatora C2920

Ponowna definicja: "class": szablon klasy lub typ ogólny został już zadeklarowany jako "type"

Klasa generyczny lub szablonu ma wiele deklaracji, które nie są równoważne. Aby naprawić ten błąd, użyj innej nazwy dla różnych typów, lub usuń ponowna definicja nazwę typu.

Poniższy przykład generuje C2920 i pokazuje, jak go naprawić:

```
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

C2920 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```