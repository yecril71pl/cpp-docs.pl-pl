---
title: Błąd kompilatora C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: b9a6d9cd57572f65b24656fa527725c9c605143d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628270"
---
# <a name="compiler-error-c3215"></a>Błąd kompilatora C3215

'Typ1': parametr typu generycznego już ograniczony przez 'type2'

Ograniczenie została określona więcej niż raz.

Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [ogólne](../../windows/generics-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3215:

```
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

Możliwe rozwiązanie:

```
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```