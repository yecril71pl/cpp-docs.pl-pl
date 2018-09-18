---
title: Błąd kompilatora C2250 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2250
dev_langs:
- C++
helpviewer_keywords:
- C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bee638b3e716460f54def3dc347810c874706708
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070135"
---
# <a name="compiler-error-c2250"></a>Błąd kompilatora C2250

'Identyfikator': niejednoznaczne dziedziczenie "class::member"

Klasa pochodna dziedziczy więcej niż jeden przesłonięcie funkcji wirtualnej z wirtualnej klasy bazowej. Te zastąpienia są niejednoznaczne w klasie pochodnej.

Poniższy przykład spowoduje wygenerowanie C2286:

```
// C2250.cpp
// compile with: /c
// C2250 expected
struct V {
   virtual void vf();
};

struct A : virtual V {
   void vf();
};

struct B : virtual V {
   void vf();
};

struct D : A, B {
   // Uncomment the following line to resolve.
   // void vf();
};
```