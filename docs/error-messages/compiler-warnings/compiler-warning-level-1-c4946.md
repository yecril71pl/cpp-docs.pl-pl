---
title: Kompilator ostrzeżenie (poziom 1) C4946 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4946
dev_langs:
- C++
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7186848ffc005721fca430d53558100789eae76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086658"
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