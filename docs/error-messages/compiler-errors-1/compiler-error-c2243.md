---
title: Błąd kompilatora C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ded5a3d459e4b5d1412998aadbaa385864f505a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445555"
---
# <a name="compiler-error-c2243"></a>Błąd kompilatora C2243

'conversion type' konwersja z 'Typ1' na 'Typ2' istnieje, ale jest niedostępna

Dostęp do ochrony (`protected` lub `private`) uniemożliwił konwersja ze wskaźnika do klasy pochodnej na wskaźnik do klasy bazowej.

Poniższy przykład spowoduje wygenerowanie C2243:

```
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

Podstawowa klasach z atrybutem `protected` lub `private` dostępu nie są dostępne dla klientów w klasie pochodnej. Te poziomy kontroli dostępu są używane do wskazania, że klasy bazowej jest szczegół implementacji, które powinny być niewidoczne na klientach. Użyj publicznego pochodnym, jeśli chcesz, aby klienci klasy pochodnej na dostęp do niejawna konwersja wskaźnika klasy pochodnej na wskaźnik do klasy bazowej.