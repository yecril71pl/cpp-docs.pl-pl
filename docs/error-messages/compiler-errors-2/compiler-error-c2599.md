---
title: Błąd kompilatora C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: 872c3a66d4738c1a69990dffdbbc59cee9e90002
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544641"
---
# <a name="compiler-error-c2599"></a>Błąd kompilatora C2599

"enum": deklaracja typu wyliczenia jest niedozwolone.

Kompilator nie obsługuje już deklaracją do przodu zarządzanych wyliczenia.

Deklaracja typu wyliczeniowego jest niedozwolona w [/Za](../../build/reference/za-ze-disable-language-extensions.md).

Poniższy przykład spowoduje wygenerowanie C2599:

```
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```