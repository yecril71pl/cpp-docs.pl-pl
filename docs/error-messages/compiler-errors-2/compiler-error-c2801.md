---
title: Błąd kompilatora C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: cfb89c79534318ab1fbcaa06667d594bfe2f1157
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214597"
---
# <a name="compiler-error-c2801"></a>Błąd kompilatora C2801

operator "operator" musi być niestatyczną składową

Następujące operatory mogą być przeciążone tylko jako niestatyczne elementy członkowskie:

- Wykorzystując`=`

- Dostęp do elementu członkowskiego klasy`->`

- Tworzenie indeksów dolnych`[]`

- Wywołanie funkcji`()`

Możliwe przyczyny C2801:

- Przeciążony operator nie jest klasą, strukturą ani składową Unii.

- Zadeklarowano przeciążony operator **`static`** .

- Poniższy przykład generuje C2801:

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
