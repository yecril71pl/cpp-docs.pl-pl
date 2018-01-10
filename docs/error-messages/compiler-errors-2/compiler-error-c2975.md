---
title: "C2975 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2975
dev_langs: C++
helpviewer_keywords: C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f779ec2623b6b07f61c1e8347304288d0bcfe96a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2975"></a>C2975 błąd kompilatora

> "*argument*": nieprawidłowy argument szablonu dla "*typu*", oczekiwano stałego wyrażenia czasu kompilacji

Argument szablonu nie jest zgodna deklaracja szablonu; wyrażenie stałe powinny być wyświetlane w nawiasach kwadratowych kąta. Zmienne nie są dozwolone jako argumenty rzeczywiste szablonu. Sprawdź definicję szablonu, aby znaleźć poprawne typy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2975 i przedstawiono również poprawne użycie:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 występuje również w przypadku gdy używasz &#95; &#95; WIERSZ &#95; &#95; jako Stała kompilacji z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md). Jedno rozwiązanie byłoby kompilacji z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) zamiast **/zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```