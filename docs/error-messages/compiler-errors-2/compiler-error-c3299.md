---
title: Błąd kompilatora C3299 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ca5a57ca1cdfe442386872d738a01cf4235685c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117832"
---
# <a name="compiler-error-c3299"></a>Błąd kompilatora C3299

"member_function": nie można określić ograniczeń, są one dziedziczone z metody podstawowej

Podczas zastępowania funkcja ogólnej składowej, nie można określić ograniczenia klauzule (powtarzające się ograniczenia oznacza, że ograniczenia nie są dziedziczone).

Klauzule ograniczenia na ogólnych funkcji, które są zastępowanie będą dziedziczone.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3299.

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```