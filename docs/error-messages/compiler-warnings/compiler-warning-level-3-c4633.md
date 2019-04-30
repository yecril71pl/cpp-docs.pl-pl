---
title: Kompilator ostrzeżenie (poziom 3) C4633
ms.date: 11/04/2016
f1_keywords:
- C4633
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
ms.openlocfilehash: 039489a804bb5d2bd17186b22bcfb8bea644c377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401738"
---
# <a name="compiler-warning-level-3-c4633"></a>Kompilator ostrzeżenie (poziom 3) C4633

Docelowy komentarza dokumentu XML: błąd: Przyczyna

Nazwa przekazana do [ \<param >](../../build/reference/param-visual-cpp.md) przez kompilator nie znaleziono tagu.

Poniższy przykład spowoduje wygenerowanie C4633:

```
// C4633.cpp
// compile with: /clr /doc /LD /W3

/// Text for class MyClass.
public ref class MyClass {
   // C4633 remove line for Int3
   /// <param name="Int1">Used to indicate status.</param>
   /// <param name="Int3">Used to indicate status.</param>
   void MyMethod(int Int1) {
      Int1 = 0;
      Int1++;
   }
};
```