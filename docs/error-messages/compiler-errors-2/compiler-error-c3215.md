---
title: Błąd kompilatora C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 24f17d2990c9258168a6d37fef101c21f62cb08d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778725"
---
# <a name="compiler-error-c3215"></a>Błąd kompilatora C3215

'Typ1': parametr typu generycznego już ograniczony przez 'type2'

Ograniczenie została określona więcej niż raz.

Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [ogólne](../../extensions/generics-cpp-component-extensions.md).

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