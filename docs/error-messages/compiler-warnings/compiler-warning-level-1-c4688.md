---
title: Ostrzeżenie kompilatora (poziom 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: e7aebfa3ae602aa45c02897711cd94520a876cca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175405"
---
# <a name="compiler-warning-level-1-c4688"></a>Ostrzeżenie kompilatora (poziom 1) C4688

"Constraint": Lista ograniczeń zawiera prywatny Typ zestawu "Type"

Lista ograniczeń ma typ prywatny zestawu, co oznacza, że nie będzie ona dostępna, gdy do typu zostanie uzyskany dostęp spoza zestawu. Aby uzyskać więcej informacji, zobacz [Ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4688.

```cpp
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```
