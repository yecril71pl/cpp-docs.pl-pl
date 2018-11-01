---
title: Błąd kompilatora C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446036"
---
# <a name="compiler-error-c2027"></a>Błąd kompilatora C2027

Użycie niezdefiniowanego typu "type"

Nie można użyć typu, jeśli nie jest zdefiniowana. Aby naprawić błąd, upewnij się, że typ jest w pełni zdefiniowana przed odwołaniem się do niej.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2027.

```
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>Przykład

Istnieje możliwość zadeklarować wskaźnik do typu zadeklarowana ale niezdefiniowana.  Ale Visual C++ nie zezwala na odwołanie do niezdefiniowanego typu.

Poniższy przykład spowoduje wygenerowanie C2027.

```
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```