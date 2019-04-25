---
title: Kompilator ostrzeżenie (poziom 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: f215c621486bf223d8f6c90b0a4f4ae119ad4b1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280574"
---
# <a name="compiler-warning-level-1-c4946"></a>Kompilator ostrzeżenie (poziom 1) C4946

reinterpret_cast używane między pokrewnymi klasami: 'klasa1' i 'klasa2'

Nie używaj [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) do rzutowania między typami powiązane. Użyj [static_cast](../../cpp/static-cast-operator.md) zamiast tego lub typach polimorficznych, użyj [dynamic_cast](../../cpp/dynamic-cast-operator.md).

Domyślnie to ostrzeżenie jest wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy kod generuje C4946:

```
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```