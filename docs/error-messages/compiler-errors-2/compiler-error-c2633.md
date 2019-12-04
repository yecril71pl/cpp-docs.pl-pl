---
title: Błąd kompilatora C2633
ms.date: 11/04/2016
f1_keywords:
- C2633
helpviewer_keywords:
- C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
ms.openlocfilehash: a2e4ca81194968fb50a5442cab3d229a25b8be1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754683"
---
# <a name="compiler-error-c2633"></a>Błąd kompilatora C2633

"Identyfikator": "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów

Konstruktor jest zadeklarowany jako Klasa magazynu inna niż inline.

Poniższy przykład generuje C2633:

```cpp
// C2633.cpp
// compile with: /c
class C {
   extern C();   // C2633, not inline
   inline C();   // OK
};
```
