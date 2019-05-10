---
title: Błąd kompilatora C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447994"
---
# <a name="compiler-error-c2603"></a>Błąd kompilatora C2603

> "*funkcja*": Zbyt wiele bloku statycznych obiektów w zakresie z konstruktorem/destruktorami w funkcji

W wersjach programu Microsoft C++ kompilatora przed Visual Studio 2015, lub gdy [threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) — opcja kompilatora jest określony, jest ograniczona do 31 liczby obiektów statycznych, które mogą mieć w widocznego na zewnątrz Funkcja śródwierszowa.

Aby rozwiązać ten problem, firma Microsoft zaleca, przyjmuje nowszą wersję programu Microsoft C++ zestaw narzędzi kompilatora, lub jeśli jest to możliwe, Usuń threadsafeinit — opcja kompilatora. Jeśli nie jest to możliwe, należy wziąć pod uwagę łączenia obiektów statycznych. Jeśli obiekty są tego samego typu, rozważ użycie jednej tablicy statycznej tego typu, a następnie odwoływać się do poszczególnych elementów członkowskich, zgodnie z potrzebami.

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
