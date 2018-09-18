---
title: Błąd kompilatora C2920 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2920
dev_langs:
- C++
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd8d28cf0f201b3042fe3d7a13d28e56150c976e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021606"
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