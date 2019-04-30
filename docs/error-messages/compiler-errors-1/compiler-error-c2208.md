---
title: Błąd kompilatora C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 7970ba5d8d2b19bd6e330fad1879880fc5cbf32d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400451"
---
# <a name="compiler-error-c2208"></a>Błąd kompilatora C2208

"type": Brak składowych zdefiniowanych przy użyciu tego typu

Identyfikator rozpoznawania nazwy typu znajduje się w deklaracji agregacji, ale kompilator nie może zadeklarować członka.

Poniższy przykład spowoduje wygenerowanie C2208:

```
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```