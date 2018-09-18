---
title: Błąd kompilatora C2897 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2897
dev_langs:
- C++
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d05663b913a3e310c091b62a81483f28bbf2c09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049835"
---
# <a name="compiler-error-c2897"></a>Błąd kompilatora C2897

destruktor/finalizator nie może być szablonem funkcji

Destruktory i finalizatory nie mogą być przeciążone, więc zadeklarowanie destruktora jako szablon (który zdefiniuje zbiór destruktory) nie jest dozwolone.

Poniższy przykład spowoduje wygenerowanie C2897:

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2897.

```
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2897.

```
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```