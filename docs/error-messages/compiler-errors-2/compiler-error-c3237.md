---
title: Błąd kompilatora C3237
ms.date: 11/04/2016
f1_keywords:
- C3237
helpviewer_keywords:
- C3237
ms.assetid: 690970c8-e13b-4ff3-96e3-5fd93c4d356b
ms.openlocfilehash: 9c0c65cba83fd1dfed09d3aeba75d7deac9218c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759376"
---
# <a name="compiler-error-c3237"></a>Błąd kompilatora C3237

"generic_class": Klasa generyczna nie może być atrybutem niestandardowym

Klasy generyczne nie mogą być atrybutami zdefiniowanymi przez użytkownika.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3237.

```cpp
// C3237.cpp
// compile with: /clr /c
// C3237 expected
using namespace System;

generic <class T>
// Delete the following line to resolve.
[attribute(AttributeTargets::All, AllowMultiple=true)]
public ref class GR {};
```
