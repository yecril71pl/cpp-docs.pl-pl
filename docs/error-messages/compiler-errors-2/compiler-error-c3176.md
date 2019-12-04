---
title: Błąd kompilatora C3176
ms.date: 11/04/2016
f1_keywords:
- C3176
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
ms.openlocfilehash: c6e25d119846c7209ead5d3fe7e19b6273bf8583
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761702"
---
# <a name="compiler-error-c3176"></a>Błąd kompilatora C3176

"Type": nie można zadeklarować lokalnego typu wartościowego

Klasa może być zadeklarowana jako typ wartości tylko w zakresie globalnym.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3176.

```cpp
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```
