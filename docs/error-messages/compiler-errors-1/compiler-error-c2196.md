---
title: Błąd kompilatora C2196
ms.date: 11/04/2016
f1_keywords:
- C2196
helpviewer_keywords:
- C2196
ms.assetid: fd2f6a58-48ce-4e58-96f8-e37720feb8e7
ms.openlocfilehash: ec677e14b856f4b8a572006d61668ef089e42834
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758518"
---
# <a name="compiler-error-c2196"></a>Błąd kompilatora C2196

wartość Case "value" została już użyta.

Instrukcja Switch używa tej samej wartości case więcej niż raz.

Poniższy przykład generuje C2196:

```cpp
// C2196.cpp
int main() {
   int i = 0;
   switch( i ) {
   case 0:
      break;
   case 0:   // C2196
   // try the following line instead
   // case 1:
      break;
   }
}
```
