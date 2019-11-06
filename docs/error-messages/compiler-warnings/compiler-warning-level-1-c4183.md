---
title: Ostrzeżenie kompilatora (poziom 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: be79c664f09f80d8f0c8779babf236dccac90ea8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626231"
---
# <a name="compiler-warning-level-1-c4183"></a>Ostrzeżenie kompilatora (poziom 1) C4183

"Identyfikator": Brak typu zwracanego; przyjęto, że jest funkcją członkowską zwracającą wartość "int"

Wbudowana definicja funkcji składowej w klasie lub strukturze nie ma zwracanego typu. Przyjęto, że ta funkcja członkowska ma domyślny zwracany typ `int`.

Poniższy przykład generuje C4183:

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```