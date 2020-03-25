---
title: Ostrzeżenie kompilatora (poziom 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 5d6e89efb042b8f757feec3911b160961e51f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199696"
---
# <a name="compiler-warning-level-1-c4624"></a>Ostrzeżenie kompilatora (poziom 1) C4624

"Klasa pochodna": destruktor został niejawnie zdefiniowany jako usunięty, ponieważ destruktor klasy bazowej jest niedostępny lub usunięty

Destruktor nie był dostępny ani usunięty w klasie bazowej i dlatego nie został wygenerowany dla klasy pochodnej. Każda próba utworzenia obiektu tego typu na stosie spowoduje błąd kompilatora.

Poniższy przykład generuje C4624 i pokazuje, jak to naprawić:

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```
