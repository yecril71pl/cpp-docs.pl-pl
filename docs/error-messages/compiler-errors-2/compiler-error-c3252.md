---
title: Błąd kompilatora C3252 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70a38090bcbe1a984e643d6d995abe2c79339163
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080626"
---
# <a name="compiler-error-c3252"></a>Błąd kompilatora C3252

"method": nie można zredukować dostępności wirtualnej metody w zarządzanej lub typu WinRT

Klasa, która implementuje metodę wirtualną z klasy bazowej lub metody w interfejsie nie można zmniejszyć dostępu do tej metody.

Należy pamiętać, że wszystkie metody w interfejsie są publiczne.

Poniższy przykład generuje C3252 i pokazuje, jak go naprawić:

```
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```