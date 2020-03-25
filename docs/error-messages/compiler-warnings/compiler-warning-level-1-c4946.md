---
title: Ostrzeżenie kompilatora (poziom 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: 3b829eb7cdd0adc58a3ddb225115a4b188a2336f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199077"
---
# <a name="compiler-warning-level-1-c4946"></a>Ostrzeżenie kompilatora (poziom 1) C4946

reinterpret_cast używane między pokrewnymi klasami: 'klasa1' i 'klasa2'

Nie należy używać [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) do rzutowania między powiązanymi typami. Zamiast tego użyj [static_cast](../../cpp/static-cast-operator.md) lub dla typów polimorficznych Użyj [dynamic_cast](../../cpp/dynamic-cast-operator.md).

Domyślnie to ostrzeżenie jest wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład kodu generuje C4946:

```cpp
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
