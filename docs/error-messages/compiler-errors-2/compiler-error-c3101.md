---
title: Błąd kompilatora C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: dca91b9359417b8c4cce9329e2aa25107016c086
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750003"
---
# <a name="compiler-error-c3101"></a>Błąd kompilatora C3101

niedozwolone wyrażenie nazwanego argumentu atrybutu "pole"

Podczas inicjowania nazwanego argumentu atrybutu wartość musi być stałą czasu kompilacji.

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3101.

```cpp
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
