---
title: Kompilator ostrzeżenie (poziom 4) C4623 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4623
dev_langs:
- C++
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: beb890483db5ef9e979f6eb790f811ae6822e42b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118599"
---
# <a name="compiler-warning-level-4-c4623"></a>Kompilator ostrzeżenie (poziom 4) C4623

"`derived class`": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty, ponieważ domyślny konstruktor klasy bazowej jest niedostępny lub usunięty

Konstruktor nie jest dostępna w klasie bazowej i nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba utworzenia obiektu tego typu na stosie.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4623.

```
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```