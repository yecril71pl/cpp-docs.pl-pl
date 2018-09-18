---
title: Błąd kompilatora C2603 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2603
dev_langs:
- C++
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a893a77fb3760f00fb7fe7b5cb3ce5b3db3346e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057683"
---
# <a name="compiler-error-c2603"></a>Błąd kompilatora C2603

> "*funkcja*": zbyt wiele bloku statycznych obiektów w zakresie z konstruktorem/destruktorami w funkcji

W wersji kompilatora Visual C++ przed Visual Studio 2015 lub gdy [threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) — opcja kompilatora jest określony, jest ograniczona do 31 liczby obiektów statycznych, które mogą mieć w widocznego na zewnątrz wbudowanej funkcji .

Aby rozwiązać ten problem, zaleca się przyjmują nowsze wersje zestawu narzędzi kompilatora Visual C++, lub jeśli jest to możliwe, Usuń threadsafeinit — opcja kompilatora. Jeśli nie jest to możliwe, należy wziąć pod uwagę łączenia obiektów statycznych. Jeśli obiekty są tego samego typu, rozważ użycie jednej tablicy statycznej tego typu, a następnie odwoływać się do poszczególnych elementów członkowskich, zgodnie z potrzebami.

## <a name="example"></a>Przykład

Poniższy kod generuje C2603 i pokazano jeden ze sposobów, aby rozwiązać ten problem:

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
