---
title: Kompilator ostrzeżenie (poziom 4) C4339 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4339
dev_langs:
- C++
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab96374beffed9822b20f4f10db812f170ea6cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025233"
---
# <a name="compiler-warning-level-4-c4339"></a>Kompilator ostrzeżenie (poziom 4) C4339

"type": użycie niezdefiniowanego typu wykryte w WinRT, czy CLR meta-data - użycie tego typu może prowadzić do wyjątku czasu wykonywania

Typ nie został zdefiniowany w kodzie, który został skompilowany dla środowiska uruchomieniowego Windows lub środowisko uruchomieniowe języka wspólnego. Zdefiniuj typ, aby uniknąć wyjątek czasu wykonywania to możliwe.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład generuje C4339 i pokazuje, jak go naprawić:

```
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```