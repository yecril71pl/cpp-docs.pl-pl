---
title: Błąd kompilatora C2243 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5d3a6c20ff147ac2a4b765c7779cec9f19627e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102232"
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