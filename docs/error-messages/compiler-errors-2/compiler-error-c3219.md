---
title: Błąd kompilatora C3219
ms.date: 11/04/2016
f1_keywords:
- C3219
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
ms.openlocfilehash: a93e9ed1a8e00eaecc664bda02a70c81b6c81ded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243040"
---
# <a name="compiler-error-c3219"></a>Błąd kompilatora C3219

"param": parametr generyczny nie może być ograniczony przez wiele elementów niebędących interfejsami: "class"

Nie jest prawidłowy w celu ograniczenia parametru ogólnego, przez co najmniej dwóch klas zarządzanych.

Poniższy przykład spowoduje wygenerowanie C3219:

```
// C3219.cpp
// compile with: /clr
ref class A {};
ref class B {};

generic <class T>
where T : A, B
ref class E {};   // C3219
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3219b.cpp
// compile with: /clr /c
ref class A {};

interface struct C {};

generic <class T>
where T : A
ref class E {};
```