---
title: Błąd kompilatora C2657 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2657
dev_langs:
- C++
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 342b336582b7920756a17b99f0d52dcb28c7173a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109980"
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