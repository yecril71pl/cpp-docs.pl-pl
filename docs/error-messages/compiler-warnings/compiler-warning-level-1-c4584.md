---
title: Kompilator ostrzeżenie (poziom 1) C4584 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9db97bf35034f7ca628f860924bfb9a1fccc942f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036257"
---
# <a name="compiler-warning-level-1-c4584"></a>Kompilator ostrzeżenie (poziom 1) C4584

'klasa1': klasy podstawowej 'klasa2' jest już klasą bazową "class3"

Klasa, zdefiniowanych przez Ciebie dziedziczy z dwóch klas, w jednym z nich dziedziczy po drugiej. Na przykład:

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

W tym przypadku ostrzeżenie będzie wygenerowane klasy C ponieważ dziedziczy on zarówno z klasy A i B, który również dziedziczy z klasy A. klasy To ostrzeżenie służy jako monitu, czy należy całkowicie Zakwalifikuj użycie członków z tych klas bazowych lub błąd kompilatora, które zostaną wygenerowane z powodu niejednoznaczności do składowej klasy, które można znaleźć.