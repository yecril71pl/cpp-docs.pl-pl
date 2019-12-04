---
title: Błąd kompilatora C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: f5a62b1c12b94735d0383697bf7a92d12d64b21f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757803"
---
# <a name="compiler-error-c2243"></a>Błąd kompilatora C2243

Konwersja "typ konwersji" z "type1" na "type2" istnieje, ale jest niedostępna

Ochrona dostępu (`protected` lub `private`) uniemożliwiła konwersję ze wskaźnika do klasy pochodnej na wskaźnik do klasy bazowej.

Poniższy przykład generuje C2243:

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Klasy bazowe z dostępem `protected` lub `private` są niedostępne dla klientów klasy pochodnej. Te poziomy kontroli dostępu są używane do wskazywania, że klasa podstawowa jest szczegółami implementacji, które powinny być niewidoczne dla klientów. Użyj publicznej metody tworzenia, jeśli chcesz, aby klienci klasy pochodnej mieli dostęp do niejawnej konwersji wskaźnika klasy pochodnej na wskaźnik do klasy bazowej.
