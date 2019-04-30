---
title: Kompilator ostrzeżenie (poziom 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: dd150621ad3474444861982c095ae8a6addb52fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404042"
---
# <a name="compiler-warning-level-1-c4489"></a>Kompilator ostrzeżenie (poziom 1) C4489

"specyfikatora": niedozwolony dla metody interfejsu "method"; zastąpienie specyfikatorów są dozwolone tylko dla metod klasy ref i klas wartości

Słowo kluczowe specyfikator niepoprawnie została użyta wobec metody interfejsu.

Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4489.

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```