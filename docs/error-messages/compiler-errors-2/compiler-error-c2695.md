---
title: Błąd kompilatora C2695 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2695
dev_langs:
- C++
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a618c02fcf3a8927d8090b1ad51ed16d9ac28542
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056056"
---
# <a name="compiler-error-c2695"></a>Błąd kompilatora C2695

"function1": przesłanianie wirtualnej funkcji różni się od "function2" tylko konwencją wywołania

Podpis funkcji w klasie pochodnej nie może przesłonić funkcji w klasie bazowej i zmień konwencji wywoływania.

Poniższy przykład spowoduje wygenerowanie C2695:

```
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```