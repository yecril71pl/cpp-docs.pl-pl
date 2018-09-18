---
title: Błąd kompilatora C2675 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1772f6e88516e7c8c1498f84d180ab6c4e0e05ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102409"
---
# <a name="compiler-error-c2675"></a>Błąd kompilatora C2675

Jednoargumentowy "operator": "type" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora

C2675 może również wystąpić, gdy za pomocą operatora jednoargumentowego, a typ nie posiada zdefiniowanego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora. Użycie operatora, możesz go przeciążenia dla określonego typu lub zdefiniuj konwersji na typ, dla którego zdefiniowano operator.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2675.

```
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```