---
title: Błąd kompilatora C2473 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2473
dev_langs:
- C++
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0eeecedd3ad2cee551b6003912d9b7af32883588
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026078"
---
# <a name="compiler-error-c2473"></a>Błąd kompilatora C2473

'Identyfikator': wygląda jak definicja funkcji, ale nie ma żadnej listy parametrów.

Kompilator wykrył wyglądał jak funkcje, bez listy parametrów.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2473.

```
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```