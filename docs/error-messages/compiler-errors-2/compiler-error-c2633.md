---
title: Błąd kompilatora C2633
ms.date: 11/04/2016
f1_keywords:
- C2633
helpviewer_keywords:
- C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
ms.openlocfilehash: 746f01706c7c0ec09a64c5faee748f9582ac9a14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367762"
---
# <a name="compiler-error-c2633"></a>Błąd kompilatora C2633

'Identyfikator': "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów

Konstruktor jest zadeklarowany jako klasy magazynu innym niż wbudowany.

Poniższy przykład spowoduje wygenerowanie C2633:

```
// C2633.cpp
// compile with: /c
class C {
   extern C();   // C2633, not inline
   inline C();   // OK
};
```