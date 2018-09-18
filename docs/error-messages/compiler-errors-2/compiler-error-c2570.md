---
title: Błąd kompilatora C2570 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2570
dev_langs:
- C++
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5914af21ec780167c45334829a5d6517cf3662
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052988"
---
# <a name="compiler-error-c2570"></a>Błąd kompilatora C2570

'Identyfikator': Unia nie może mieć klas bazowych

Unia pochodzi z klasy, struktury lub Unii. Jest to niedozwolone. Zamiast deklarowania typu pochodnego jako klasę lub strukturę.

Poniższy przykład spowoduje wygenerowanie C2570:

```
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```