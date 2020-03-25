---
title: Ostrzeżenie kompilatora (poziom 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: e9811e9f9c17463fdcd550ffd82af4f81a40bb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186611"
---
# <a name="compiler-warning-level-1-c4489"></a>Ostrzeżenie kompilatora (poziom 1) C4489

Specyfikator ": niedozwolony dla metody interfejsu" Method "; Specyfikatory przesłonięcia są dozwolone tylko w metodach klasy referencyjnej i klasie wartości

Słowo kluczowe specyfikatora zostało nieprawidłowo użyte w metodzie interfejsu.

Aby uzyskać więcej informacji, zobacz [specyfikatory przesłonięć](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4489.

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```
