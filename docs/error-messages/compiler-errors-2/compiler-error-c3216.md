---
title: Błąd kompilatora C3216
ms.date: 11/04/2016
f1_keywords:
- C3216
helpviewer_keywords:
- C3216
ms.assetid: bbab1efe-8779-4489-8bb0-b11e45f5cbe5
ms.openlocfilehash: 80435c38ff4130938c996b1144aa71300f96eca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311543"
---
# <a name="compiler-error-c3216"></a>Błąd kompilatora C3216

ograniczenie musi być parametrem generycznym, nie "type"

Ograniczenie został niewłaściwie sformatowany.

Poniższy przykład spowoduje wygenerowanie C3216:

```
// C3216.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where F : A   // C3216
// Try the following line instead:
// where T : A    // C3216
ref class C {};
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3216b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```