---
title: Błąd kompilatora C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360440"
---
# <a name="compiler-error-c2657"></a>Błąd kompilatora C2657

"klasa:: *" znaleziono w chwili rozpoczęcia instrukcji (Czy pamiętasz o określeniu typu?)

Wiersz rozpoczęło się o identyfikatorze wskaźników do elementów członkowskich.

Ten błąd może być spowodowany przez brak specyfikatora typu w deklaracji wskaźnika do elementu członkowskiego.

Poniższy przykład spowoduje wygenerowanie C2657:

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```