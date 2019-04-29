---
title: Błąd kompilatora C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 08f74bf635324ed9a05c13ecf532862d58e4f0b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368191"
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