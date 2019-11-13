---
title: Ostrzeżenie kompilatora (poziom 1) C4661
ms.date: 11/04/2016
f1_keywords:
- C4661
helpviewer_keywords:
- C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
ms.openlocfilehash: d9d608c0e9baf05c327e17fa7159e25e27fb5cf3
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051409"
---
# <a name="compiler-warning-level-1-c4661"></a>Ostrzeżenie kompilatora (poziom 1) C4661

"Identyfikator": brak odpowiedniej definicji dostarczonej dla jawnego żądania wystąpienia szablonu

Nie zdefiniowano elementu członkowskiego klasy szablonu.

## <a name="example"></a>Przykład

```cpp
// C4661.cpp
// compile with: /W1 /LD
template<class T> class MyClass {
public:
   void i();   // declaration but not definition
};
template MyClass< int >;  // C4661
```