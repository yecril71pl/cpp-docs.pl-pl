---
title: Ostrzeżenie kompilatora (poziom 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 5b31fd22c917b2c0f505ca189425f8160f62f748
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175548"
---
# <a name="compiler-warning-level-1-c4677"></a>Ostrzeżenie kompilatora (poziom 1) C4677

"Function": Sygnatura nieprywatnej składowej zawiera prywatny Typ zestawu "private_type"

Typ z publiczną dostępnością poza zestawem korzysta z typu, który ma prywatny dostęp poza zestawem. Składnik, który odwołuje się do typu zestawu publicznego, nie będzie mógł używać składowej typu lub składowych odwołujących się do typu prywatnego zestawu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4677.

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```
