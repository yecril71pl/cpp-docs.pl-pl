---
title: Błąd kompilatora C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ab0dbe8c5595c18a01f78c22056803dce91a3f31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212842"
---
# <a name="compiler-error-c2243"></a>Błąd kompilatora C2243

Konwersja "typ konwersji" z "type1" na "type2" istnieje, ale jest niedostępna

Ochrona dostępu ( **`protected`** lub **`private`** ) uniemożliwiła konwersję ze wskaźnika do klasy pochodnej na wskaźnik do klasy bazowej.

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

Klasy bazowe z **`protected`** lub **`private`** dostępu są niedostępne dla klientów klasy pochodnej. Te poziomy kontroli dostępu są używane do wskazywania, że klasa podstawowa jest szczegółami implementacji, które powinny być niewidoczne dla klientów. Użyj publicznej metody tworzenia, jeśli chcesz, aby klienci klasy pochodnej mieli dostęp do niejawnej konwersji wskaźnika klasy pochodnej na wskaźnik do klasy bazowej.
