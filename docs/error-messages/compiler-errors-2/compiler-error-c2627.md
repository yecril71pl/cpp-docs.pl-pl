---
title: Błąd kompilatora C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: dc976a0c16d19d1fd2340676e43eb71903163aa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222861"
---
# <a name="compiler-error-c2627"></a>Błąd kompilatora C2627

'Funkcja': funkcja składowa nie jest dozwolona w anonimowej Unii

[Anonimowej Unii](../../cpp/unions.md#anonymous_unions) nie może mieć elementów członkowskich.

Poniższy przykład spowoduje wygenerowanie C2627:

```
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```