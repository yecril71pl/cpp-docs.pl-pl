---
title: Błąd kompilatora C3856 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3856
dev_langs:
- C++
helpviewer_keywords:
- C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfe4a53e9d2f48dab479fa9403ede5c8a8c4a1b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098241"
---
# <a name="compiler-error-c3856"></a>Błąd kompilatora C3856

"type": klasa nie jest typem klasy

Najczęstszą przyczyną tego błędu jest, gdy istnieją bardziej ogólny lub parametr szablonu wymieniono w punkcie definicji nie istniały w punkcie deklaracji.

Poniższy przykład spowoduje wygenerowanie C3856:

```
// C3856.cpp
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>   // C3856
template <class T1>
template <class T2>  // extra template parameter list in definition
struct S<T>::S1{};
```

Możliwe rozwiązanie:

```
// C3856b.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1{};
```

C3856 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3856c.cpp
// compile with: /clr
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GS<T>::GS2 {};   // C3856
```

Możliwe rozwiązanie:

```
// C3856d.cpp
// compile with: /clr /c
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
ref struct GS<T>::GS2 {};
```